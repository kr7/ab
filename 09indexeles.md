# Adatok generálása indexek hatásának kipróbálásához

```
import java.sql.*;

public String nev() {
  String[] csnev = new String[] { "Kovacs", "Horvath", "Smith",
          "Iclanzan", "Nemeth", "Szabo", "Nagy", "Kis"};
  String[] knev = new String[] {"Anna", "Peter", "Eva", "Adam",
          "Daniel", "Napsugar", "Hanna", "Laszlo", "Noemi"};
  char c = (char)(65+Math.random()*26);
  return csnev[(int)(Math.random() * csnev.length)] + " " +
          c+". " + knev[(int)(Math.random() * knev.length)];
}

public int tel() {
  return (int)(Math.random()*10000000);
}

public String email(String nev) {
  String e1 = nev.replaceAll(" ",".");
  return e1.replaceAll("\\.\\.",".")+"@gmail.com";
}

void main() {
  try ( Connection con = DriverManager.getConnection(
          "jdbc:mysql://localhost:3306/pekseg",
          "hallgato", "h411gato");
        Statement stmt = con.createStatement();
  ) {
    for (int i = 0; i<1000000; i++) {
      String n = nev();
      String t = Integer.toString(tel());
      String e = email(n);
      String sql = "insert into ugyfelek values ('"+n+"','"+t+"','"+e+"')";
      //System.out.println(sql);
      stmt.execute(sql);
    }
  } catch (Exception e) {
    e.printStackTrace();
  }
}
```

Próbáljunk ki kereső jellegű lekérdezéseket, pl.
```
select * from ugyfelek where email = 'bela@gmail.com';
```
indexek használatával és anélkül.

Indexek létrehozása:
```
create index EmailSzerintiIndex on ugyfelek(email);
create index NevSzerintiIndex on ugyfelek(nev);
create index TelSzerintiIndex on ugyfelek(tel);
```
