### 1) Java’da `static block` ve `static initializer` nedir?

Bir sınıf JVM tarafından **ilk kez yüklendiğinde** çalıştırılan özel bloklardır.  
`static` alanları (sınıfa ait değişkenleri) başlatmak için kullanılırlar.  
Bir sınıf için **sadece bir kez** çalışırlar ve **constructor’lardan önce** yürütülürler.

```java
class Demo {
    static int count;
    static {
        count = 10;
        System.out.println("Static block çalıştı");
    }
}
```

---

### 2) Bir constructor’dan başka bir constructor nasıl çağrılır?

Aynı sınıf içindeki başka bir constructor’ı çağırmak için `this()` kullanılır.

Kurallar:

- `this()` **ilk satırda** olmalı.
    
- Bir constructor içinde **yalnızca bir tane** `this()` çağrısı olabilir.
    

```java
class Car {
    Car() { this("Default"); }
    Car(String name) { System.out.println(name); }
}
```

---

### 3) Method Overriding nedir?

Bir **alt sınıf**, üst sınıfta tanımlanmış bir metodu **aynı imza** (isim + parametre tipi + dönüş tipi) ile yeniden tanımlarsa buna **overriding** denir.  
Amaç, **farklı davranış** kazandırmaktır.  
Çağrı **runtime**’da (çalışma zamanında) hangi nesne tipine aitse o versiyon çalışır.

---

### 4) `super` anahtar kelimesi nedir?

`super`, alt sınıftan üst sınıfın **değişkenlerine, metotlarına veya constructor’ına** erişmek için kullanılır.  
İki biçimde kullanılır:

- `super()` → üst sınıfın constructor’ını çağırır (ilk satırda olmalı).
    
- `super.variable` veya `super.method()` → üst sınıfın üyesine erişir.
    

---

### 5) Overloading vs Overriding farkı nedir?

|Özellik|Overloading|Overriding|
|---|---|---|
|Tanım|Aynı sınıfta, aynı isimli ama **farklı parametreli** metotlar|Üst ve alt sınıflarda, **aynı imzalı** metotlar|
|İlişki|Aynı sınıf içinde|İki sınıf (inheritance) arasında|
|Dönüş tipi|Farklı olabilir|Aynı olmalı (ya da covariant)|
|Zaman|Compile-time (statik polimorfizm)|Runtime (dinamik polimorfizm)|

---

### 6) Abstract class ve Interface farkı nedir?

|Özellik|Interface|Abstract Class|
|---|---|---|
|Metotlar|Tümü abstract (Java 8+ ile default/static de olabilir)|Abstract ve concrete metotlar olabilir|
|Değişkenler|`public static final` zorunlu|Her erişim düzeyi olabilir|
|Miras|Çoklu kalıtım sağlanabilir|Tekli kalıtım|
|Kullanım|“Ne yapılacağını” tanımlar|“Nasıl yapılacağını” kısmen tanımlar|

---

### 7) Java neden platform bağımsızdır?

Çünkü derleme sonrası oluşan `.class` dosyası **bytecode** içerir.  
Bytecode’u çalıştıran **JVM (Java Virtual Machine)**, her platformda farklıdır ama bytecode sabittir.  
Bu nedenle “**Write Once, Run Anywhere**” prensibi geçerlidir.

---

### 8) Method Overloading nedir?

Aynı sınıfta aynı isimli ama **farklı parametre listelerine** sahip metotlar tanımlamaktır.  
Derleme zamanında hangi versiyonun çağrılacağı **parametre tipi/sayısına göre** belirlenir.

```java
void add(int a, int b);
void add(double a, double b);
```

---

### 9) C++ ve Java farkları nelerdir?

|Özellik|Java|C++|
|---|---|---|
|Platform|Bağımsız (JVM sayesinde)|Platforma bağımlı|
|Pointer|Yok (güvenlik için)|Var|
|Operator overloading|Desteklenmez|Desteklenir|
|Garbage collection|Otomatik|Manuel|
|Multithreading|Dahili destek var|Yok|
|Global değişken|Yok|Var|

---

### 10) JIT Compiler nedir?

**Just-In-Time Compiler**, JVM’in bir parçasıdır.  
Bytecode’u yürütülmeden hemen önce **makine koduna** çevirir.  
Yani program tamamen derlenmez; sadece **ihtiyaç duyulan kısımlar** çalıştırma anında derlenir → performansı artırır.

---

### 11) Bytecode nedir?

`javac` derleyicisi bir `.java` dosyasını derlediğinde, ortaya `.class` uzantılı bir **bytecode** dosyası çıkar.  
Bu dosya, **makineye özel değil**, JVM’in anlayacağı bir **ara kod** (intermediate code)’dur.  
Yani bytecode = “Java’nın evrensel dili”.  
JVM bu bytecode’u her platformda makine koduna çevirerek çalıştırır.

---

### 12) `this()` ve `super()` farkı nedir?

- `this()` → **Aynı sınıf** içindeki başka bir constructor’ı çağırır.
    
- `super()` → **Üst sınıfın constructor’ını** çağırır.
    

Her ikisi de constructor’ın **ilk satırında** olmalıdır; aksi halde derleme hatası alınır.

---

### 13) Class (sınıf) nedir?

Sınıf, Java’daki **nesne yönelimli programlamanın temelidir**.  
Bir sınıf, bir nesnenin **özelliklerini (fields)** ve **davranışlarını (methods)** tanımlar.  
Bir tür “şablon” veya “plan” gibi düşün.

```java
public class Araba {
    String marka;
    void calistir() { System.out.println("Motor çalıştı"); }
}
```

---

### 14) Object (nesne) nedir?

Nesne, bir sınıfın **örneğidir (instance)**.  
Bellekte gerçek bir varlık oluşturur.  
Her nesnenin **durumu (state)** ve **davranışı (behavior)** vardır.

```java
Araba a = new Araba(); // 'a' bir Araba nesnesi
a.calistir(); // Nesne davranışını çağırır
```

---

### 15) Method nedir?

Bir metot, belirli bir işi yapan kod bloğudur.  
Sınıf içinde tanımlanır.  
İsmi, dönüş tipi, parametre listesi ve gövdesi vardır.

```java
int topla(int a, int b) {
    return a + b;
}
```

---

### 16) Encapsulation (kapsülleme) nedir?

Veriyi (**fields**) ve bu veriyle ilgili işlemleri (**methods**) tek bir sınıfta toplamak, ve dışarıdan doğrudan erişimi **kontrol altına almak**.  
Yani “veriyi gizle, sadece kontrollü erişim sağla.”

```java
class Ogrenci {
    private String isim; // gizli veri
    public void setIsim(String isim) { this.isim = isim; }
    public String getIsim() { return isim; }
}
```

Bu yapı, hem **güvenliği artırır** hem de **bakımı kolaylaştırır**.

---

### 17) `main()` metodu neden `public static void` olarak tanımlanır?

- `public` → JVM, sınıf dışından bu metodu çağırabilsin diye.
    
- `static` → JVM’in sınıfı başlatmak için **nesne oluşturmadan** çağırabilmesi için.
    
- `void` → `main()` metodu herhangi bir değer döndürmez.
    

Yani JVM, `public static void main(String[] args)` imzasını **otomatik olarak arar**.

---

### 18) `main()` metodunun önemi nedir?

Java uygulamasında **çalışma başlangıç noktasıdır**.  
Programın yürütmesi `main()` içinde başlar.  
Parametre olarak `String[] args` alır; bu, **komut satırından** gelen argümanları taşır.

---

### 19) Constructor (yapıcı metod) nedir?

Bir sınıftan nesne oluşturulduğunda **otomatik olarak çağrılan özel metot**tur.  
Nesnenin ilk değerlerini ayarlamak için kullanılır.  
Constructor’ın ismi **sınıf adıyla aynı olmalıdır** ve dönüş tipi **olmaz**.

```java
class Araba {
    Araba() { System.out.println("Araba oluşturuldu"); }
}
```

- **Default constructor**: Parametresiz.
    
- **Parameterized constructor**: Parametre alır.
    

---

### 20) `length` ve `length()` farkı nedir?

- `length()` → **String** sınıfında bir metottur.  
    Karakter sayısını döndürür.
    
    ```java
    String s = "Hello";
    s.length(); // 5
    ```
    
- `length` → **Array (dizi)** için bir **özelliktir (field)**.  
    Dizinin eleman sayısını verir.
    
    ```java
    int[] sayilar = {1,2,3};
    sayilar.length; // 3
    ```
    

---

### 21) ASCII kodu nedir?

**ASCII (American Standard Code for Information Interchange)**, bilgisayarlarda karakterleri sayısal olarak temsil etmek için geliştirilmiş 7-bitlik bir karakter kümesidir.  
Karakter aralığı: **0 – 255**  
Örnek:

- `'A'` → 65
    
- `'a'` → 97
    

ASCII sadece **İngilizce karakterleri** destekler. Türkçe, Çince gibi dillerdeki özel karakterleri kapsamaz.

---

### 22) Unicode nedir?

**Unicode**, tüm dillerin karakterlerini kapsamak için geliştirilmiş evrensel bir karakter kodlamasıdır.  
Java, tüm karakterleri **Unicode (UTF-16)** biçiminde temsil eder.  
Karakter aralığı: **0 – 65,535 (2^16 - 1)**

Bu yüzden Java’da `'ç'`, `'ü'`, `'你'` gibi karakterler de rahatlıkla kullanılabilir.  
Örneğin:

```java
char c = '\u00E7'; // ç karakteri
```

---

### 23) Character Constant ve String Constant farkı nedir?

**Character Constant (karakter sabiti):**

- Tek tırnak içinde tanımlanır: `'A'`, `'7'`, `'\n'`
    
- Türü: `char`
    
- Tek bir karakteri temsil eder.
    

**String Constant (dizge sabiti):**

- Çift tırnak içinde tanımlanır: `"A"`, `"Hello"`
    
- Türü: `String`
    
- Birden fazla karakteri (dizi) temsil eder.
    

---

### 24) Constant (sabit) nedir, nasıl oluşturulur?

Sabitler, program boyunca **değeri değiştirilemeyen değişkenlerdir**.  
Java’da sabitler `final` anahtar kelimesiyle tanımlanır.

```java
final int MAX_SPEED = 120;
final String APP_NAME = "MyApp";
```

Bir kez atanırlar, sonrasında değiştirilemezler.

---

### 25) `>>` ve `>>>` operatörleri arasındaki fark nedir?

Her ikisi de **bit kaydırma operatörüdür**, ama fark şudur:

- `>>` → **Signed Right Shift**  
    Negatif sayılarda sol taraftaki boşlukları **işaret bitiyle (1)** doldurur.  
    Yani işaret korunur.
    
- `>>>` → **Unsigned Right Shift**  
    Sol taraftaki boşlukları **0** ile doldurur.  
    Negatiflik bilgisi korunmaz.
    

Örnek:

```java
int x = -8;
System.out.println(x >> 2);   // -2
System.out.println(x >>> 2);  // 1073741822
```

---

### 26) Java’da sınıflar için kodlama standartları nelerdir?

Oracle’ın önerdiği **Java Coding Conventions**’a göre:

- Sınıf isimleri **büyük harfle** başlar.
    
- Her kelimenin ilk harfi büyük olmalıdır (PascalCase).
    
- İsimler genelde **isim (noun)** olmalıdır.
    

Örnek:  
`Employee`, `CarDetails`, `StringBuilder`

---

### 27) Interface’ler için kodlama standartları nelerdir?

- Interface isimleri de **büyük harfle** başlar.
    
- Genellikle **sıfat (adjective)** veya **yetenek belirtici** isimlerdir.
    

Örnek:  
`Runnable`, `Serializable`, `Cloneable`, `Comparable`

---

### 28) Metotlar için kodlama standartları nelerdir?

- Küçük harfle başlar.
    
- İçinde birden fazla kelime varsa, ikinci kelimeden itibaren büyük harf kullanılır (**camelCase**).
    
- Genellikle **fiil (verb)** ile başlar.
    

Örnek:  
`getName()`, `calculateSalary()`, `toString()`

---

### 29) Değişkenler için kodlama standartları nelerdir?

- Küçük harfle başlar.
    
- Anlamlı, kısa ve okunabilir olmalıdır.
    
- Birden fazla kelimeli isimlerde camelCase kullanılır.
    

Örnek:  
`count`, `totalAmount`, `employeeName`

---

### 30) Sabitler (constants) için kodlama standartları nelerdir?

- Genellikle `public static final` olarak tanımlanır.
    
- Tüm harfler **büyük** yazılır.
    
- Kelimeler **alt çizgi (`_`)** ile ayrılır.
    

Örnek:  
`MAX_VALUE`, `PI`, `DEFAULT_PORT`

---

### 31) Overriding ve Overloading farkı nedir?

|Özellik|**Overriding**|**Overloading**|
|---|---|---|
|Tanım|Üst sınıfta tanımlı bir metodu, alt sınıfta **aynı imzayla yeniden tanımlamak**|Aynı isimli metodu **farklı parametrelerle** tanımlamak|
|İlişki|İki sınıf (inheritance ilişkisi) arasında olur|Aynı sınıf içinde olur|
|Dönüş tipi|Aynı olmalı veya **covariant** olabilir|Farklı olabilir|
|Polimorfizm tipi|**Runtime (dinamik)**|**Compile-time (statik)**|
|Exception kuralları|Checked exception seviyesi artırılamaz|Herhangi bir exception atanabilir|
|Erişim|Üst sınıftakinden daha kısıtlı olamaz|Fark etmez|

Kısaca:  
**Overriding** davranışı değiştirir,  
**Overloading** aynı davranışı farklı girdilerle genişletir.

---

### 32) “IS-A” ilişkisi nedir?

“IS-A” ilişkisi, **inheritance (kalıtım)** demektir.  
Bir sınıf, başka bir sınıfın alt türü ise, “X is a Y” şeklinde ifade edilir.

Örnek:

```java
class Vehicle {}
class Car extends Vehicle {}
```

Burada **Car IS-A Vehicle** — yani “Araba bir Taşıttır”.  
Avantajı: Kodun **yeniden kullanılabilirliği (reusability)** artar.

---

### 33) “HAS-A” ilişkisi nedir?

“HAS-A” ilişkisi, **composition (bileşim)** veya **aggregation (ilişki)** demektir.  
Bir sınıf, başka bir sınıfı **üye değişken olarak içeriyorsa**, bu ilişki vardır.

Örnek:

```java
class Engine {}
class Car {
    Engine engine = new Engine(); // Car HAS-A Engine
}
```

Burada “Araba bir motora sahiptir” deriz.  
Avantajı yine kodun **yeniden kullanılabilirliğidir**, ama miras yerine **iç içe nesneler** kullanılır.

---

### 34) IS-A ve HAS-A farkı nedir?

|Özellik|IS-A|HAS-A|
|---|---|---|
|Tür|Kalıtım (extends)|Kompozisyon / Agregasyon|
|Anahtar kelime|`extends`|`new` (veya dependency injection)|
|Örnek|`Car extends Vehicle`|`Car has an Engine`|
|Odak|“Bir türüdür”|“Bir parçasıdır”|
|Avantaj|Kodun yeniden kullanımı (davranış mirası)|Esneklik, bileşen tabanlı yapı|

---

### 35) `instanceof` operatörü nedir?

Bir nesnenin hangi sınıfa ait olduğunu kontrol eder.  
Sonuç **boolean** döner.  
Sözdizimi:

```java
obj instanceof ClassName
```

Örnek:

```java
String s = "Hello";
System.out.println(s instanceof String); // true
```

Eğer referans `null` ise sonuç her zaman `false` döner.  
Derleme zamanında tip kontrolü yapılır, yanlış türler hata verir.

---

### 36) `null` ne anlama gelir?

Bir referansın **hiçbir nesneyi göstermediğini** ifade eder.  
Yani “boş” değil, “hiç yok”.

```java
String name = null;
System.out.println(name.length()); // NullPointerException
```

`null`, yalnızca **referans türleri** için geçerlidir (primitive’ler için değil).

---

### 37) Bir dosyada birden fazla sınıf olabilir mi?

Evet, bir `.java` dosyasında **birden fazla sınıf** tanımlanabilir, ama:

- Yalnızca **bir tanesi public** olabilir.
    
- Public sınıfın adı **dosya adıyla aynı** olmalıdır.
    

```java
class A {}
class B {}
public class Main {} // Dosya adı: Main.java
```

---

### 38) Üst seviye (top-level) sınıflar için hangi access modifier’lar kullanılabilir?

Sadece iki tanesi geçerlidir:

- **public** → Her yerden erişilebilir.
    
- **default (hiçbiri yazılmaz)** → Sadece **aynı paket** içinden erişilir.
    

`private` veya `protected` olarak tanımlarsan derleme hatası alırsın.  
Hata: _“Illegal modifier for the class”_

---

### 39) Package (paket) nedir?

**Paket**, ilişkili sınıf, interface ve enum’ları bir araya getiren **mantıksal grup** yapısıdır.  
Kodun düzenli ve modüler olmasını sağlar.

Sözdizimi:

```java
package com.company.project;
```

Amaçlar:

1. İsim çakışmalarını önlemek (namespace kontrolü)
    
2. Erişim kontrolü (visibility)
    
3. Kodun organize edilmesi
    

---

### 40) Bir dosyada birden fazla `package` tanımlanabilir mi?

Hayır.  
Bir `.java` dosyasında **sadece bir tane package bildirimi** bulunabilir.  
Bu ifade her zaman **ilk satırda** olmalıdır.  
Aksi takdirde derleyici hata verir.

---

### 41) `package` ifadesi `import` ifadesinden sonra tanımlanabilir mi?

Hayır.  
`package` bildirimi bir `.java` dosyasının **ilk satırında** olmalıdır.  
Yalnızca **yorum satırları** ondan önce gelebilir.  
`import` ifadesi her zaman **`package`’den sonra** gelir.

Örnek:

```java
// doğru
package com.example;
import java.util.List;
```

Aksi halde derleyici hatası alınır:

> “Package declaration must be the first statement in the source file.”

---

### 42) Java’da identifier (tanımlayıcı) nedir?

Bir değişkenin, metodun, sınıfın veya paketin adıdır.  
Kısaca — kod içindeki “isimler”dir.

Kurallar:

- Harf, `_` veya `$` ile başlayabilir.
    
- Sayı ile **başlayamaz**.
    
- Büyük/küçük harf duyarlıdır. (`Name` ≠ `name`)
    
- Java anahtar kelimeleri (`class`, `public` vb.) kullanılamaz.
    

Örnekler:  
✅ `userName`, `_temp`, `$data`  
❌ `2value`, `public`, `#age`

---

### 43) Access modifier (erişim belirleyici) nedir?

Java’da erişim belirleyiciler (access modifiers), **sınıf, metot ve değişkenlerin** görünürlüğünü belirler.

Dört tür vardır:

- `public` → Her yerden erişilebilir.
    
- `private` → Sadece aynı sınıf içinden erişilebilir.
    
- `protected` → Aynı paket içinden ve alt sınıflardan erişilebilir.
    
- (hiçbiri yazılmazsa) → **default erişim**: sadece aynı paket içinden erişilebilir.
    

Bu yapı Java’nın **encapsulation (kapsülleme)** modelini sağlar.

---

### 44) Access specifier ile access modifier farkı nedir?

C++’ta bunlar ayrı kavramlardır, fakat Java’da **ayrım yoktur**.  
Java’da “access modifier” terimi hem erişim seviyesini hem de bazı davranışsal nitelikleri kapsar.

- **Access modifiers:** `public`, `private`, `protected`, _(default)_
    
- **Non-access modifiers:** `final`, `abstract`, `static`, `strictfp` vb.
    

---

### 45) Sınıflarda hangi access modifier’lar kullanılabilir?

Yalnızca iki tanesi geçerlidir:

1. `public` → Her yerden erişilebilir.
    
2. (hiçbiri yazılmaz) → **default**, sadece aynı paket içinden erişilebilir.
    

Sınıflar için `private` veya `protected` **kullanılamaz.**

---

### 46) Metotlar için hangi access modifier’lar kullanılabilir?

Tümü (`public`, `private`, `protected`, `default`) kullanılabilir.

- `public` → Her yerden erişim.
    
- `protected` → Aynı paket veya alt sınıf erişimi.
    
- `default` → Aynı paket içinden erişim.
    
- `private` → Sadece tanımlandığı sınıf içinden erişim.
    

Bu kurallar, miras (inheritance) sırasında erişilebilirliği belirler.

---

### 47) Değişkenler için hangi access modifier’lar kullanılabilir?

Yine dört erişim seviyesi mümkündür (`public`, `private`, `protected`, `default`).

- **public:** Her yerden erişilebilir.
    
- **protected:** Aynı paket + alt sınıflar.
    
- **default:** Aynı paket.
    
- **private:** Sadece aynı sınıf.
    

Değişkenlerde `private` en çok tercih edilen düzeydir, çünkü veriyi dışarıdan korur.

---

### 48) `final` access modifier nedir?

`final`, “değiştirilemez” anlamındadır. Üç yerde kullanılabilir:

1. **final class** → Kalıtılamaz (örneğin `String` sınıfı).
    
2. **final method** → Override edilemez.
    
3. **final variable** → Değeri değiştirilemez (sabit olur).
    

Örnek:

```java
final int MAX_SPEED = 180;
final void start() {}
final class Vehicle {}
```

Avantaj: Güvenlik  
Dezavantaj: Esneklik azalır (polimorfizm kısıtlanır).

---

### 49) `abstract` class nedir?

Bazı metotların gövdesi olmadan tanımlandığı, **soyut** bir sınıftır.  
Amaç: Alt sınıfların kendi implementasyonlarını zorunlu kılmaktır.

Özellikleri:

- **Abstract metot** içerebilir.
    
- **Concrete (normal)** metotlar da içerebilir.
    
- **Nesnesi oluşturulamaz**.
    
- Alt sınıflar, abstract metotları **override etmek zorundadır.**
    

Örnek:

```java
abstract class Vehicle {
    abstract void start();
    void stop() { System.out.println("Stop"); }
}
```

---

### 50) `abstract` sınıfta constructor tanımlanabilir mi?

Evet, tanımlanabilir.  
Ancak doğrudan **nesne oluşturulamadığı** için constructor sadece **alt sınıflar tarafından çağrılabilir.**

```java
abstract class Animal {
    Animal() { System.out.println("Animal constructor"); }
}

class Dog extends Animal {
    Dog() { super(); }
}
```

Yani, abstract sınıfın constructor’ı **kalıtım sırasında** çalışır ama **doğrudan** çağrılamaz.

---

### 51) Abstract method (soyut metot) nedir?

**Abstract method**, yalnızca bildirimi olan ama **gövdesi (body)** bulunmayan metottur.  
Bu metodun **gerçek davranışı**, alt sınıfta tanımlanmak zorundadır.

Sözdizimi:

```java
public abstract void draw();
```

Özellikler:

- Sadece **abstract class** veya **interface** içinde tanımlanabilir.
    
- Gövdesiz olduğu için **`;`** ile biter.
    
- Abstract sınıflar içinde **0 veya daha fazla** abstract metot bulunabilir.
    

Amaç: Alt sınıfları **belirli davranışları zorunlu kılmaya** yönlendirmek.

---

### 52) Java’da exception (istisna) nedir?

Bir program çalışırken **beklenmedik bir durum oluştuğunda** JVM tarafından atılan veya programcı tarafından fırlatılan **nesnedir**.  
Tüm exception sınıfları `java.lang.Exception` sınıfından türemiştir.

Örnek durumlar:

- 0’a bölme → `ArithmeticException`
    
- Dizi sınırı aşımı → `ArrayIndexOutOfBoundsException`
    
- Dosya bulunamadı → `FileNotFoundException`
    

Kısaca: Exception = “Çalışma zamanında meydana gelen anormal durum”.

---

### 53) Exception hangi durumlarda oluşabilir?

Bazı tipik örnekler:

1. Dizi elemanına geçersiz indeksle erişim
    
2. String → int dönüşüm hatası (`NumberFormatException`)
    
3. Geçersiz tür dönüşümü (`ClassCastException`)
    
4. Interface veya abstract class’tan nesne oluşturmaya çalışma (`InstantiationException`)
    

---

### 54) Exception handling nedir?

Bir hata meydana geldiğinde programın **durmaması**, bunun yerine uygun biçimde yönetilmesidir.  
Amaç: Programın **normal akışını korumak.**

`try-catch-finally` yapısı ile yapılır.

```java
try {
    int x = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Sıfıra bölünemez!");
} finally {
    System.out.println("Temizlik yapıldı.");
}
```

---

### 55) Java’da “error” nedir?

**Error**, `Throwable` sınıfının `Exception` dışındaki alt sınıfıdır.  
Programcı tarafından **yakalanması amaçlanmaz**, çünkü sistem seviyesidir.

Örnek:

- `OutOfMemoryError`
    
- `StackOverflowError`
    

Kısaca:

- **Exception** → Program hatası (yönetilebilir)
    
- **Error** → Sistem hatası (kritik, toparlanamaz)
    

---

### 56) Exception handling’in avantajları nelerdir?

1. Hataları kodun geri kalanından **ayırır**, temiz kontrol sağlar.
    
2. Farklı türde hataları ayrı ayrı ele alabilmeyi sağlar.
    
3. Hataların **çağrı zinciri boyunca aktarılmasına (propagation)** izin verir.
    
4. Programın **çökmek yerine kontrollü devam etmesini** sağlar.
    

---

### 57) Java’da exception handling kaç şekilde yapılabilir?

İki temel yöntem vardır:

1. **try-catch-finally** kullanmak  
    → Exception’ı orada yakalayıp işlem yapmak.
    
2. **throws** anahtar kelimesiyle atmak  
    → Exception’ı bir üst metoda fırlatmak (sorumluluğu devretmek).
    

---

### 58) Exception handling ile ilgili beş anahtar kelime nedir?

Java’nın exception mekanizması beş temel keyword’e dayanır:

- `try` → Riskli kod bloğu
    
- `catch` → Hata yakalama bloğu
    
- `throw` → Manuel exception fırlatma
    
- `throws` → Exception’ı üst metoda devretme
    
- `finally` → Her durumda çalışan temizlik bloğu
    

---

### 59) `try` ve `catch` blokları nasıl çalışır?

`try` bloğunda hataya yol açabilecek kodlar yer alır.  
Eğer hata oluşursa, JVM uygun `catch` bloğuna yönlendirir.

Örnek:

```java
try {
    int[] arr = {1, 2};
    System.out.println(arr[3]);
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Dizi sınırı aşıldı!");
}
```

- Eğer exception oluşmazsa `catch` atlanır.
    
- Eğer oluşursa `catch` bloğu çalışır ve program devam eder.
    

---

### 60) `try` bloğu `catch` olmadan kullanılabilir mi?

Evet, ama **yalnızca `finally`** varsa.  
Yani `try` bloğu tek başına olamaz, en az bir **catch** veya **finally** içermelidir.

Geçerli:

```java
try {
    System.out.println("Deneme");
} finally {
    System.out.println("Her durumda çalışır");
}
```

Geçersiz:

```java
try {
    System.out.println("Olmaz");
}
// Derleme hatası: “try without catch or finally”
```

---

### 61) Tek bir `try` bloğu için birden fazla `catch` bloğu olabilir mi?

Evet.  
Bir `try` bloğu, farklı türdeki hataları **farklı `catch` bloklarında** yakalayabilir.  
Java, hatanın türüne göre **uygun olan ilk `catch` bloğunu** çalıştırır.

```java
try {
    int[] arr = new int[2];
    arr[3] = 10;
} catch (ArrayIndexOutOfBoundsException e) {
    System.out.println("Dizi sınırı aşıldı");
} catch (Exception e) {
    System.out.println("Genel hata");
}
```

**Dikkat:**  
`catch` blokları **alt sınıftan üst sınıfa doğru** sıralanmalıdır.  
Aksi halde derleme hatası olur (“Exception has already been caught”).

---

### 62) `finally` bloğunun önemi nedir?

`finally` bloğu, **istisna oluşsa da oluşmasa da** her zaman çalışır.  
Genellikle şu işler için kullanılır:

- Kaynakların kapatılması (`close()` çağrıları)
    
- Bağlantıların serbest bırakılması (dosya, socket, DB)
    
- Temizlik işlemleri
    

```java
try {
    System.out.println(10 / 0);
} catch (Exception e) {
    System.out.println("Hata!");
} finally {
    System.out.println("Finally her zaman çalışır.");
}
```

---

### 63) `try` ve `catch` blokları arasında kod yazılabilir mi?

Hayır, yazılamaz.  
`catch` bloğu **hemen `try` bloğunun ardından** gelmelidir.  
Aksi halde derleyici hata verir.

Geçersiz örnek:

```java
try {
    System.out.println("Deneme");
}
System.out.println("Bu satır hata verir");
catch (Exception e) {
    System.out.println("Hata!");
}
```

---

### 64) `try` ve `finally` blokları arasında kod yazılabilir mi?

Hayır, yazılamaz.  
`finally` bloğu da `try` (veya `catch`) bloğundan **hemen sonra** gelmelidir.

Geçerli:

```java
try {
    System.out.println("İşlem");
} finally {
    System.out.println("Temizlik");
}
```

Geçersiz:

```java
try {
    System.out.println("İşlem");
}
System.out.println("Araya kod yazmak yasak"); // Hata!
finally {
    System.out.println("Temizlik");
}
```

---

### 65) Tek bir `catch` bloğunda birden fazla exception yakalanabilir mi?

Evet, **Java 7** ile birlikte bu özellik geldi.  
Aynı işlemle yönetilecek birden fazla istisna türünü tek bir `catch`’te birleştirebilirsin.

```java
try {
    int x = Integer.parseInt("abc");
} catch (NumberFormatException | NullPointerException e) {
    System.out.println("Birden fazla hata türü yakalandı.");
}
```

Not:

- `catch` parametresi **otomatik olarak `final`** olur; yeniden atanamaz.
    

---

### 66) Checked exception nedir?

**Derleme zamanında kontrol edilen** istisnalardır.  
Programcı, bu tür istisnaları **ya yakalamak (`try-catch`)** ya da **fırlatmak (`throws`)** zorundadır.

Örnekler:

- `IOException`
    
- `SQLException`
    
- `FileNotFoundException`
    
- `ClassNotFoundException`
    

Eğer bu tür bir istisna yakalanmaz veya `throws` edilmezse → **compile-time error** oluşur.

---

### 67) Unchecked exception nedir?

**Derleme zamanında kontrol edilmeyen**, sadece çalışma zamanında ortaya çıkan istisnalardır.  
Bunlar `RuntimeException` sınıfından türeyen hatalardır.

Örnekler:

- `NullPointerException`
    
- `ArrayIndexOutOfBoundsException`
    
- `ArithmeticException`
    
- `NumberFormatException`
    

Bu tür istisnaları yakalamak **zorunlu değildir** — ama yakalamak programın sağlamlığını artırır.

---

### 68) Checked ve Unchecked exception farkı nedir?

|Özellik|Checked|Unchecked|
|---|---|---|
|Kontrol zamanı|Derleme zamanında|Çalışma zamanında|
|Zorunlu yakalama|Evet (`try-catch` veya `throws`)|Hayır|
|Sınıf kökeni|`Exception` (ama `RuntimeException` hariç)|`RuntimeException` ve alt sınıfları|
|Örnekler|`IOException`, `SQLException`|`NullPointerException`, `ArithmeticException`|

---

### 69) Default exception handling nedir?

Bir istisna yakalanmadığında **JVM’in kendisinin devreye girip** olayı yönetmesidir.  
JVM şunları yapar:

1. İstisna nesnesini oluşturur.
    
2. Türünü, açıklamasını ve oluştuğu satırı yazar.
    
3. Stack trace’i ekrana basar.
    
4. Programı **sonlandırır**.
    

Dezavantaj:  
Program **ani şekilde durur**, bu yüzden kendi `try-catch` mekanizmamızı kurmamız önerilir.

---

### 70) `throw` anahtar kelimesi nedir?

Kendin manuel olarak bir exception **fırlatmak** için kullanılır.  
Yani JVM’in otomatik fırlatmasına gerek kalmadan, sen kendi istisnanı oluşturabilirsin.

Sözdizimi:

```java
throw new Exception("Kullanıcı tanımlı hata");
```

Kurallar:

- Sadece **bir exception nesnesi** fırlatılabilir.
    
- `throw` kullanıldıktan sonra, o satırdan sonraki kod **çalışmaz**.
    
- Eğer `checked exception` fırlatıyorsan, metot imzasına `throws` eklenmelidir.
    

---

### 71) `throw` ifadesinden sonra kod yazılabilir mi?

Hayır, yazılamaz.

Bir `throw` ifadesi çalıştığında, JVM akışı **hemen sonlandırır** ve exception fırlatılır.  
Sonraki hiçbir satır yürütülmez.

Örnek:

```java
throw new ArithmeticException("Hata!");
System.out.println("Bu satır asla çalışmaz."); // Derleme hatası: unreachable code
```

Derleyici bunu fark eder ve “unreachable code” hatası verir.

---

### 72) `throws` anahtar kelimesinin önemi nedir?

`throws`, bir metodun **hangi istisnaları fırlatabileceğini** belirtir.  
Yani: “Ben bu hatayı burada yakalamıyorum, çağıran kod ilgilensin” demektir.

Sözdizimi:

```java
void okuDosya() throws IOException {
    FileReader f = new FileReader("data.txt");
}
```

Kullanım amacı:

- Checked exception’ları üst metoda devretmek.
    
- Metodun exception politikalarını açıkça belirtmek.
    

`throws` yalnızca **`Throwable` türünden** sınıflarla kullanılabilir (`Exception`, `Error` veya alt sınıfları).

---

### 73) `finally` ve `return` çatışırsa ne olur?

`finally` **her zaman çalışır**, `return` ifadesinden bile önce.  
Yani hem `try` hem `catch` içinde `return` olsa bile, JVM önce `finally` bloğunu yürütür.

Örnek:

```java
int test() {
    try {
        return 1;
    } finally {
        System.out.println("Finally çalıştı");
    }
}
```

Konsol çıktısı:

```
Finally çalıştı
```

Ve metot `1` döner.  
Yani `finally`, `return`’dan **önceliklidir.**

---

### 74) `finally` bloğunun çalışmayacağı bir durum var mı?

Evet, yalnızca JVM kapatılırsa.  
Örneğin `System.exit(0)` çağrıldığında, JVM tamamen kapanır ve `finally` **çalışmaz.**

```java
try {
    System.exit(0);
} finally {
    System.out.println("Bu yazı asla görünmez!");
}
```

Normal durumlarda (exception oluşsa bile) `finally` bloğu her zaman yürür.

---

### 75) Checked exception’lar için `catch` bloğu kullanılabilir mi?

Evet, ama yalnızca o exception’ın **oluşma ihtimali** varsa.  
Eğer bir checked exception’ın oluşma olasılığı **yoksa**, onu `catch`’le yakalamaya çalışmak **derleme hatası** verir.

Örnek:

```java
try {
    int x = 10 / 2;
} catch (IOException e) { } // HATA: IOException asla oluşmaz
```

---

### 76) User-defined (kullanıcı tanımlı) exception nedir?

Java’da kendi özel hata türlerini oluşturabilirsin.  
Bu, genellikle **iş mantığına özgü hataları** belirtmek için yapılır.

Bir user-defined exception oluşturmak için:

1. `Exception` (checked) veya `RuntimeException` (unchecked) sınıfını genişlet.
    
2. İsteğe bağlı olarak constructor tanımla.
    

Örnek:

```java
class AgeException extends Exception {
    AgeException(String msg) {
        super(msg);
    }
}
```

Kullanım:

```java
if (age < 18) {
    throw new AgeException("Yaş 18'den küçük olamaz!");
}
```

Tavsiyem:  
Kritik olmayan durumlarda `RuntimeException`’dan türetmek daha uygundur.

---

### 77) Bir `catch` bloğunda yakalanan exception yeniden fırlatılabilir mi?

Evet.  
`catch` içinde yakalanan istisna, aynı ya da farklı türde bir istisna olarak yeniden `throw` edilebilir.  
Bu işleme **rethrowing** denir.

```java
try {
    int x = 10 / 0;
} catch (ArithmeticException e) {
    throw e; // aynı istisnayı yeniden fırlat
}
```

Eğer checked exception yeniden fırlatılıyorsa, metot imzasına `throws` eklenmelidir.

---

### 78) Nested (iç içe) `try` blokları kullanılabilir mi?

Evet, `try` blokları **birbirinin içinde** tanımlanabilir.  
Bu, farklı hata seviyelerini yönetmek için kullanılır.

```java
try {
    try {
        int x = 10 / 0;
    } catch (ArithmeticException e) {
        System.out.println("İç try-catch");
    }
} catch (Exception e) {
    System.out.println("Dış try-catch");
}
```

İçteki `catch` exception’ı yakalayamazsa, dış `catch` devreye girer.  
Yani exception’lar **katmanlı olarak yukarı doğru** taşınır (propagation).

---

### 79) `Throwable` sınıfının önemi nedir?

`Throwable`, Java’daki **tüm hataların (Error ve Exception)** üst sınıfıdır.  
Yani her istisna türü (`IOException`, `RuntimeException`, `OutOfMemoryError` vb.) bundan türetilir.

Önemli metotlar:

- `printStackTrace()` → hatanın türü, mesajı ve oluştuğu satırları yazdırır.
    
- `getMessage()` → sadece hata mesajını döndürür.
    
- `toString()` → hata türü + mesaj döndürür.
    

Kısaca: Exception hiyerarşisinin köküdür.

---

### 80) `ClassNotFoundException` ne zaman oluşur?

Bu exception, JVM bir sınıfı **adıyla yüklemeye çalıştığında** ama o sınıf **bulunamadığında** fırlatılır.  
Genellikle `Class.forName("com.example.MyClass")` gibi refleksiyon işlemlerinde görülür.

Örnek:

```java
try {
    Class.forName("com.fake.Class");
} catch (ClassNotFoundException e) {
    System.out.println("Sınıf bulunamadı!");
}
```

Bu, checked exception’dır — yani `try-catch` veya `throws` zorunludur.

---

### 81) Process (süreç) ve Thread (iş parçacığı) arasındaki fark nedir?

**Process (süreç):**

- Kendi **bellek alanına** sahiptir.
    
- Her process birbirinden bağımsızdır.
    
- Process’ler arası iletişim zordur (IPC gerekir).
    
- Örneğin: Her açtığın Java programı ayrı bir process’tir.
    

**Thread (iş parçacığı):**

- Aynı process içinde **bellek paylaşır**.
    
- Daha hafif ve hızlıdır.
    
- Aynı anda birden fazla işi yapabilir.
    

Bir process içinde birden fazla thread çalışabilir — bunlara **çoklu iş parçacığı** denir.

---

### 82) Thread nedir?

Thread, programın içinde **bağımsız yürüyen küçük bir alt akıştır**.  
Her Java uygulaması en az bir thread ile başlar: **main thread**.

Multithreading sayesinde:

- CPU zamanı daha verimli kullanılır.
    
- Aynı anda birden fazla işlem yapılabilir.
    

Java, thread desteğini `java.lang.Thread` sınıfı ve `Runnable` arabirimi üzerinden sağlar.

---

### 83) Thread nasıl oluşturulur?

Java’da iki yöntem vardır:

1. **Thread sınıfını genişleterek:**
    
    ```java
    class MyThread extends Thread {
        public void run() {
            System.out.println("Thread çalışıyor");
        }
    }
    
    new MyThread().start();
    ```
    
2. **Runnable arayüzünü implemente ederek:**
    
    ```java
    class MyRunnable implements Runnable {
        public void run() {
            System.out.println("Runnable çalışıyor");
        }
    }
    
    new Thread(new MyRunnable()).start();
    ```
    

İkinci yöntem tercih edilir, çünkü **çoklu miras (multiple inheritance)** sorununu önler.

---

### 84) Thread nasıl başlatılır?

Bir thread’i başlatmak için `start()` metodu kullanılır.  
Bu metot JVM’e yeni bir yürütme hattı oluşturmasını söyler.

```java
MyThread t = new MyThread();
t.start(); // yeni thread başlar
```

**Dikkat:**  
`run()` metodunu doğrudan çağırmak yeni thread oluşturmaz — sadece normal bir metod çağrısı olur.

---

### 85) `start()` ve `run()` farkı nedir?

|Özellik|`start()`|`run()`|
|---|---|---|
|Amacı|Yeni thread başlatır|Thread’in çalıştırılacak kodunu tanımlar|
|Çağıran|JVM|Kullanıcı|
|Thread oluşur mu?|Evet|Hayır|
|Davranış|Paralel çalışır|Aynı thread’de çalışır|

Yani:

```java
t.start(); // Yeni thread
t.run();   // Aynı thread (main)
```

---

### 86) Thread yaşam döngüsü (lifecycle) nasıldır?

Bir thread şu beş temel durumda bulunabilir:

1. **New (Yeni)** → Henüz başlatılmadı (`new Thread()` oluşturuldu).
    
2. **Runnable** → `start()` çağrıldı, çalışmaya hazır.
    
3. **Running** → CPU tarafından yürütülüyor.
    
4. **Blocked / Waiting** → Uyku veya kilit bekliyor.
    
5. **Terminated (Ölü)** → `run()` tamamlandı.
    

Basit görsel:

```
New → Runnable → Running → (Waiting/Blocked) → Terminated
```

---

### 87) `sleep()` metodu nedir?

Bir thread’in yürütmesini belirli süre **askıya alır (bekletir)**.  
Sözdizimi:

```java
Thread.sleep(1000); // 1 saniye bekle
```

- Parametre: milisaniye (1000 = 1 saniye)
    
- Checked exception: `InterruptedException` atabilir, bu yüzden `try-catch` gerekir.
    
- Uyuyan thread, zamanı dolunca **Runnable** durumuna döner.
    

---

### 88) `yield()` metodu nedir?

`yield()`, bir thread’in geçici olarak CPU kullanım hakkını **diğer thread’lere bırakmasını** sağlar.

```java
Thread.yield();
```

Ama bu **sadece bir öneridir**, JVM bunu dikkate alıp almayacağına kendisi karar verir.  
Yani deterministik değildir — sistemin planlayıcısına (scheduler) bağlıdır.

---

### 89) `join()` metodu nedir?

Bir thread’in, başka bir thread’in bitmesini **beklemesini** sağlar.

Örnek:

```java
Thread t = new Thread(() -> System.out.println("İşlem..."));
t.start();
t.join(); // t bitmeden sonraki kod çalışmaz
System.out.println("Bitti!");
```

Bu, thread’ler arasında **senkronizasyon (sıra bekleme)** sağlar.  
Checked exception olarak `InterruptedException` fırlatabilir.

---

### 90) `isAlive()` metodu nedir?

Bir thread’in hâlâ çalışıp çalışmadığını kontrol eder.  
Sonuç **true** veya **false** döner.

```java
Thread t = new Thread(() -> {});
t.start();
System.out.println(t.isAlive()); // true (hala çalışıyor olabilir)
```

Thread tamamlandığında (`run()` bittiğinde) `isAlive()` artık `false` döner.

---

### 91) `synchronized` anahtar kelimesi nedir?

`synchronized`, birden fazla thread’in **aynı anda aynı kaynağa erişmesini engelleyen** kilitleme (locking) mekanizmasıdır.

Bir metot ya da kod bloğu `synchronized` olarak tanımlanırsa, o bölgeye aynı anda sadece **bir thread** girebilir.

```java
synchronized void print() {
    System.out.println("Tek thread girebilir");
}
```

Amaç: **race condition (yarış durumu)** denilen hatalı eşzamanlı erişimi önlemek.

---

### 92) `synchronized` nerelerde kullanılabilir?

Üç yerde kullanılabilir:

1. **Instance method** — o nesne için kilit oluşturur.
    
2. **Static method** — sınıf düzeyinde kilit oluşturur (class-level lock).
    
3. **Code block** — yalnızca belirli bir nesneye kilit uygular.
    

```java
synchronized (this) {
    // synchronized block
}
```

Bu, kilit kapsamını sınırlayarak **performans artırmak** için kullanılır.

---

### 93) Thread senkronizasyonuna neden ihtiyaç duyarız?

Çünkü aynı anda birden fazla thread aynı veriyi değiştirirse, **tutarsız sonuçlar (inconsistent state)** oluşabilir.

Örneğin:

```java
count++; // atomik değildir
```

Bu ifade üç ayrı adım içerir (okuma, artırma, yazma).  
Eğer iki thread aynı anda çalışırsa, bir artış kaybolabilir.  
`synchronized` bunu önler ve veri bütünlüğünü korur.

---

### 94) Deadlock (kilitlenme) nedir?

Deadlock, iki veya daha fazla thread’in **birbirlerinin kilidini beklerken** sonsuza kadar beklemesi durumudur.

Klasik örnek:

```java
Thread 1: lock(A) -> lock(B)
Thread 2: lock(B) -> lock(A)
```

İkisi de birbirinin kilidini bekler ve asla devam edemez.

Çözüm:

- Kilit alma sırasını belirli tutmak.
    
- `tryLock()` gibi zaman sınırlı mekanizmalar kullanmak (Java 5’ten itibaren `ReentrantLock`).
    

---

### 95) Deadlock nasıl önlenir?

1. **Kilit sırasını tutarlı yap:** Tüm thread’ler aynı kaynak sırasını izlesin.
    
2. **Zaman aşımı kullan:** `tryLock(long timeout)` ile beklemeyi sınırla.
    
3. **Kaynakları küçült:** Daha az paylaşılan veri, daha az kilit ihtiyacı.
    
4. **Synchronized bloklarını kısa tut:** Uzun süreli kilitler risklidir.
    

Deadlock önlenemezse, program **donmuş gibi görünür**.

---

### 96) Inter-thread communication (iş parçacıkları arası iletişim) nedir?

Thread’lerin birbiriyle **koordineli çalışabilmesi** anlamına gelir.  
Java’da bu iletişim `wait()`, `notify()` ve `notifyAll()` metotlarıyla sağlanır.

Amaç: Thread’ler arasında **dönüşümlü işlem** yapılmasını sağlamak.  
Örneğin, biri veri üretsin (`Producer`), diğeri tüketsin (`Consumer`).

---

### 97) `wait()`, `notify()` ve `notifyAll()` metotları nedir?

Bu metotlar **Object** sınıfına aittir (Thread değil).  
Yani Java’daki her nesne, doğal olarak bu üç metodu taşır.

- `wait()` → Thread kilidi bırakır ve bekleme moduna geçer.
    
- `notify()` → Bekleyen **bir thread’i** uyandırır.
    
- `notifyAll()` → Bekleyen **tüm thread’leri** uyandırır.
    

Kurallar:

- Bu metotlar **yalnızca synchronized blok içinde** çağrılabilir.
    
- Aksi halde `IllegalMonitorStateException` fırlatılır.
    

---

### 98) `wait()` ve `sleep()` farkı nedir?

|Özellik|`wait()`|`sleep()`|
|---|---|---|
|Tanımlı olduğu sınıf|`Object`|`Thread`|
|Kilit bırakır mı?|Evet|Hayır|
|Kullanım amacı|Thread iletişimi|Thread bekletme|
|Çağrıldığı yer|Synchronized blok içinde|Her yerde olabilir|
|Uyandırılma şekli|`notify()` veya `notifyAll()`|Süre dolunca veya interrupt|

Kısaca: `sleep()` sadece zaman kazandırır, `wait()` koordinasyon sağlar.

---

### 99) Thread priority (öncelik) nedir?

Her thread’in JVM tarafından atanan bir **öncelik değeri** vardır (`1` ile `10` arasında).  
Bu değer, CPU planlayıcısına hangi thread’in **önce çalıştırılacağı** hakkında ipucu verir.

```java
t1.setPriority(Thread.MAX_PRIORITY);
t2.setPriority(Thread.MIN_PRIORITY);
```

Ama bu **garanti değildir**; JVM veya işletim sistemi farklı davranabilir.  
Yani thread’lerin sırası tahmin edilemez — concurrency’de deterministik davranış bekleme.

---

### 100) `Thread` ve `Runnable` farkı nedir?

|Özellik|`Thread`|`Runnable`|
|---|---|---|
|Tür|Sınıf (extends)|Arayüz (implements)|
|Çoklu miras|Mümkün değil (Java tek miras destekler)|Mümkün (interface olduğundan)|
|Kullanım şekli|`class MyT extends Thread`|`class MyR implements Runnable`|
|Önerilen kullanım|Basit senaryolar|Profesyonel, ölçeklenebilir yapı|
|Avantaj|Daha kısa yazılır|Nesne tabanlı, bağımsız, esnek|

**Özet:**  
`Runnable`, modern ve doğru yaklaşımdır.  
`Thread` sınıfını doğrudan genişletmek, sadece `run()` metodu dışında miras almak için anlamlı değildir.

---

### 101) Java’da garbage collection (çöp toplama) nedir?

Garbage Collection (GC), artık kullanılmayan nesnelerin bellekte kapladığı alanı **otomatik olarak geri kazanan mekanizmadır**.  
Java’da belleği manuel olarak serbest bırakmak gerekmez; JVM bunu yapar.

Bir nesneye **hiçbir referans kalmadığında**, garbage collector onu temizler.

```java
Employee e = new Employee();
e = null; // artık erişilemez -> GC adayı
```

Avantaj: Bellek yönetimi kolaylaşır.  
Dezavantaj: GC’nin **ne zaman çalışacağı garanti edilmez.**

---

### 102) Garbage Collector ne zaman çalışır?

Kesin bir zaman yoktur. JVM, **bellek yetersizliği** durumunda veya uygun gördüğü anda çalıştırır.

Elle tetikleme mümkündür:

```java
System.gc();
```

Ama bu sadece bir **istektir**, JVM kabul etmeyebilir.

Gerçek çalışma anı **JVM iç planlayıcısına bağlıdır.**

---

### 103) Garbage Collector hangi nesneleri temizler?

GC, **hiçbir canlı referansı kalmamış** nesneleri temizler.  
Yani program tarafından artık ulaşılmayan (unreachable) nesneler.

Örnek:

```java
Car c1 = new Car();
Car c2 = new Car();
c1 = c2; // ilk Car nesnesi artık erişilemez
```

İlk oluşturulan nesne artık referanssız kaldı, GC onu temizler.

---

### 104) `finalize()` metodu nedir?

`finalize()` metodu, bir nesne garbage collector tarafından silinmeden **hemen önce** çağrılır.

Sözdizimi:

```java
protected void finalize() {
    System.out.println("Nesne toplanıyor...");
}
```

Ama dikkat:

- GC’nin **finalize()’ı ne zaman çağıracağı** garanti edilmez.
    
- Java 9 itibariyle **deprecated (kullanımı önerilmez)** hale geldi.
    

Modern Java’da bunun yerine `AutoCloseable` veya `try-with-resources` kullanılmalıdır.

---

### 105) `System.gc()` ve `Runtime.getRuntime().gc()` farkı nedir?

İkisi de aynı şeyi yapar — garbage collector’a çağrı isteği gönderir.

```java
System.gc();                 // statik yöntem
Runtime.getRuntime().gc();   // nesne üzerinden
```

Her ikisi de JVM’e “çöp toplayabilirsin” der ama **anında çalıştırmaz.**  
JVM isterse çağrıyı yok sayabilir.

---

### 106) Java’da bellek kaçağı (memory leak) olur mu?

Evet, olur.  
Garbage collector, **referans varsa** nesneyi silmez — referans gereksiz bile olsa.

Örnek:

```java
List<Object> list = new ArrayList<>();
while (true) {
    list.add(new Object()); // asla serbest bırakılmaz
}
```

Liste büyümeye devam eder → **OutOfMemoryError**.

Kısaca:  
GC sadece **referanssız** nesneleri temizler; referansı “unutulmamış” nesneleri temizlemez.

---

### 107) Stack ve Heap farkı nedir?

|Özellik|Stack|Heap|
|---|---|---|
|Kullanım|Yerel değişkenler ve metod çağrıları|Nesneler ve sınıf örnekleri|
|Bellek yönetimi|Otomatik|Garbage Collector tarafından|
|Erişim hızı|Çok hızlı|Daha yavaş|
|Yaşam süresi|Metot tamamlanana kadar|Nesne referansı kalana kadar|
|Hata türü|StackOverflowError|OutOfMemoryError|

Kısaca:

- Stack → kısa ömürlü veriler
    
- Heap → uzun ömürlü nesneler
    

---

### 108) `OutOfMemoryError` nedir?

JVM’in heap belleği dolduğunda ve yeni nesne oluşturulamadığında oluşan hatadır.

Örnek:

```java
List<int[]> list = new ArrayList<>();
while (true) {
    list.add(new int[1000000]);
}
```

Bu hata, garbage collector’ın **artık alan bulamaması** durumunda fırlatılır.  
Çözüm:

- Belleği optimize et.
    
- Gereksiz referansları kaldır.
    
- JVM heap boyutunu artır (`-Xmx1024m` gibi).
    

---

### 109) `StackOverflowError` nedir?

Bir metod çağrısı **sonsuz döngü** oluşturduğunda, çağrı yığını (stack) taşar.

Örnek:

```java
void recursive() {
    recursive(); // durmaz, stack dolar
}
```

Sonuç:

```
Exception in thread "main" java.lang.StackOverflowError
```

Bu bir **Error**’dır, **Exception** değildir.  
Genelde sonsuz özyineleme (recursion) veya çok derin çağrılar sebebiyle oluşur.

---

### 110) WeakReference nedir?

`WeakReference`, garbage collector’a “bu nesne kullanılmıyorsa temizleyebilirsin” mesajını verir.  
Yani zayıf referans, nesneyi **GC’den korumaz**.

Örnek:

```java
WeakReference<Car> weakCar = new WeakReference<>(new Car());
System.gc();
if (weakCar.get() == null)
    System.out.println("Nesne temizlendi!");
```

Kullanım amacı:

- **Cache** yapıları veya **zamanla silinebilir nesneler**.
    
- Bellek optimizasyonu yapmak.
    

---

### 111) `String` nedir, immutable olmasının anlamı

- `String`, karakter dizilerini temsil eden bir sınıftır.
    
- **Immutable** olması demek: Bir `String` oluşturulduktan sonra içeriği **değiştirilemez**.  
    Örneğin: `"Hello"`’nun karakterleri doğrudan değiştirilemez.
    
- Değişim gerekiyorsa, aslında **yeni bir String** oluşturulur.
    

Bu immutability avantaj sağlar:

- Thread-safe olurlar (çoklu iş parçacığında güvenlidir).
    
- String pool mekanizması ile bellekte paylaşım sağlanır.
    

---

### 112) `StringBuilder` ve `StringBuffer` farkı nedir?

Her ikisi de **değiştirilebilir (mutable)** karakter dizisi sınıfıdır, yani içeriğini doğrudan değiştirebilirsin.  
Ama aralarında temel farklar:

- `StringBuffer` — **synchronized (eşzamanlı erişime güvenli)**
    
- `StringBuilder` — **synchronized değil**, dolayısıyla **daha hızlı**
    

Genelde tek thread ortamında `StringBuilder` tercih edilir, çoklu thread’li durumda `StringBuffer`.

---

### 113) `String` + operatörü arka planda ne yapar?

`String`leri `+` ile birleştirdiğinde, JVM arka planda **StringBuilder** (veya StringBuffer) kullanır:

```java
String s = "Hello" + " " + "World";
```

Derleyici bunu:

```java
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.append(" ");
sb.append("World");
s = sb.toString();
```

şeklinde çevirir.  
Yani + operatörü performans açısından büyük bir dizi birleştirme için doğrudan kullanılmaz; `StringBuilder` iyidir.

---

### 114) `equals()` ve `==` arasındaki fark nedir?

- `==` → Referans karşılaştırması yapar. (İki referans aynı nesneyi mi gösteriyor?)
    
- `equals()` → İçerik karşılaştırması yapar (String’te karakter karakter eşit mi?).
    

Örnek:

```java
String a = new String("test");
String b = new String("test");
System.out.println(a == b);       // false
System.out.println(a.equals(b));  // true
```

---

### 115) `compareTo()` metodu nedir?

`Comparable` arayüzünden gelir.  
İki nesnenin **sıralama açısından** karşılaştırmasını yapar.  
String’te, sözlük sırasına göre karşılaştırır:

- Pozitif değer → `this` > parametre
    
- Negatif değer → `this` < parametre
    
- 0 → eşit
    

Örnek:

```java
"apple".compareTo("banana") // negatif değer
```

---

### 116) `String.intern()` metodu nedir?

Bu metot, String pool’da mevcut olan aynı literali döndürür ya da yoksa ekler ve onu döner.  
Amaç: Aynı içerikli String’ler bellekte tek bir nesne ile temsil edilsin.

```java
String s1 = new String("cat");
String s2 = s1.intern();
String s3 = "cat";
System.out.println(s2 == s3); // true
```

---

### 117) `String.substring()` ile memory leak olabilir mi?

Java’nın eski sürümlerinde (Java 6 öncesi) `substring()` arka planda orijinal char dizisini referans alırdı, bu da büyük orijinal String’in tamamının bellekte kalmasına yol açabilirdi.  
Yeni sürümlerde bu sorun çözülmüştür: `substring` artık yeni bir karakter dizi oluşturur, orijinal büyük diziyi referanslamaz.

---

### 118) `String` ile `StringBuilder`/`StringBuffer` karşılaştırması

- `String` immutable: değişmez, her değişim yeni nesne yaratır — performans düşer.
    
- `StringBuilder` / `StringBuffer` mutable: içeriği değiştirilebilir, değişimlerde yeni nesne yaratılmaz.
    
- `StringBuffer` güvenlidir (synchronized).
    
- `StringBuilder` tek thread ortamında daha hızlıdır.
    

---

### 119) `toString()` metodu neden override edilir?

Her sınıfın varsayılan `toString()` metodu, sınıf ismi + hash kodu verir.  
Ama okunabilir çıktı almak için çoğu sınıf bu metodu override eder:

```java
@Override
public String toString() {
    return "Person{name='" + name + "', age=" + age + "}";
}
```

Böylece `System.out.println(obj)` çağrıldığında anlamlı bilgi gösterilir.

---

### 120) `String` vs `char[]` avantajları

- `String`: Immutable, güvenli, kolay kullanım, string havuzu avantajı.
    
- `char[]`: Değiştirilebilir, hassas veriler (şifre gibi) için daha güvenli (çünkü içeriği sıfırlanabilir).
    

Örneğin, şifre dizisini `char[]` olarak saklayıp işlemden sonra silmek mümkündür, `String` ile bu öyle kolay değildir.

---

### 121) Wrapper class (sarmalayıcı sınıf) nedir?

Wrapper sınıflar, **primitive (ilkel)** veri tiplerini **nesne (object)** olarak temsil eder.  
Her primitive tipin bir wrapper sınıfı vardır:

|Primitive|Wrapper Class|
|---|---|
|`byte`|`Byte`|
|`short`|`Short`|
|`int`|`Integer`|
|`long`|`Long`|
|`float`|`Float`|
|`double`|`Double`|
|`char`|`Character`|
|`boolean`|`Boolean`|

Kullanım amacı:

- Koleksiyonlarda (`List`, `Map` vb.) primitive değerleri tutmak.
    
- Nesne tabanlı işlemler yapmak (örneğin `toString()`, `equals()` gibi metotları çağırmak).
    

---

### 122) Autoboxing nedir?

**Autoboxing**, primitive tiplerin otomatik olarak **wrapper sınıfına dönüştürülmesidir.**

```java
int x = 10;
Integer y = x; // autoboxing
```

JVM arka planda şunu yapar:

```java
Integer y = Integer.valueOf(x);
```

Bu özellik Java 5’te (JDK 1.5) eklendi.

---

### 123) Unboxing nedir?

**Unboxing**, wrapper nesnesinin primitive tipe otomatik dönüştürülmesidir.

```java
Integer i = 20;
int x = i; // unboxing
```

Derleyici arka planda:

```java
int x = i.intValue();
```

Autoboxing ve unboxing birlikte kullanıldığında, kod daha sade olur ama **performans kaybı** yaratabilir (özellikle döngülerde).

---

### 124) `Integer` ve `int` farkı nedir?

- `int`: primitive tip — stack üzerinde tutulur, hızlıdır.
    
- `Integer`: bir nesnedir (wrapper class) — heap üzerinde tutulur, metotlara sahiptir.
    

```java
int a = 5;
Integer b = 5;
System.out.println(a == b); // true (unboxing)
```

Ama dikkat:  
`Integer` objeleri `==` ile karşılaştırıldığında referans kontrolü yapılır.

---

### 125) Wrapper sınıflar immutable mı?

Evet, tüm wrapper sınıflar **immutable**’dır.  
Bir `Integer`, `Double` veya `Boolean` oluşturulduktan sonra değeri değiştirilemez.  
Değişim gibi görünen işlemler aslında **yeni nesne** oluşturur.

---

### 126) Type casting (tip dönüşümü) nedir?

Bir değişkeni başka bir tipe dönüştürmektir.  
İki tür vardır:

1. **Implicit (otomatik) casting:**  
    Küçük tip → büyük tipe (data loss yok)
    
    ```java
    int x = 10;
    double y = x; // otomatik
    ```
    
2. **Explicit (manuel) casting:**  
    Büyük tip → küçük tipe (veri kaybı olabilir)
    
    ```java
    double a = 9.7;
    int b = (int) a; // 9
    ```
    

---

### 127) Upcasting ve Downcasting nedir?

**Upcasting:** Alt sınıf nesnesini üst sınıf referansına atamaktır.  
Her zaman güvenlidir.

```java
Animal a = new Dog(); // upcasting
```

**Downcasting:** Üst sınıf referansını alt sınıfa dönüştürmektir.  
Risklidir — derleme geçer ama çalışma zamanında hata olabilir.

```java
Animal a = new Dog();
Dog d = (Dog) a; // güvenli
```

Ama:

```java
Animal a = new Cat();
Dog d = (Dog) a; // ClassCastException!
```

---

### 128) Boxing/unboxing işlemleri performansı etkiler mi?

Evet.  
Autoboxing/unboxing işlemleri **arka planda ek nesne oluşturduğu için** performansı düşürür.  
Özellikle milyonlarca sayı içeren döngülerde fark belirgindir.

Öneri:  
Performans kritik kodlarda primitive tipleri kullan.

---

### 129) `parseInt()` ve `valueOf()` farkı nedir?

Her ikisi de `String`’i sayıya dönüştürür ama fark vardır:

- `parseInt(String)` → primitive `int` döner.
    
- `valueOf(String)` → `Integer` nesnesi döner.
    

```java
int a = Integer.parseInt("10");     // primitive
Integer b = Integer.valueOf("10");  // nesne
```

---

### 130) `NumberFormatException` nedir?

Bir `String`, sayıya dönüştürülürken geçersiz formatta ise oluşur.

```java
int x = Integer.parseInt("abc"); // hata!
```

Çıktı:

```
java.lang.NumberFormatException: For input string: "abc"
```

Bu **unchecked exception**’dır (`RuntimeException` alt sınıfı).  
Yani `try-catch` zorunlu değildir ama önerilir.

---

### 131) `Object` sınıfı nedir?

Java’daki **tüm sınıfların atasıdır**.  
Her sınıf doğrudan ya da dolaylı olarak `Object` sınıfından türetilir.

Örnek:

```java
class Car {}
System.out.println(new Car() instanceof Object); // true
```

`Object` sınıfı, Java’da **her nesnenin ortak davranışlarını** tanımlar: `equals()`, `hashCode()`, `toString()`, `clone()`, `wait()`, `notify()`, `notifyAll()`…

---

### 132) `equals()` metodu neden override edilir?

Varsayılan `equals()` metodu, **referans karşılaştırması** yapar.  
Ama genelde biz **nesne içeriğini** karşılaştırmak isteriz.

Örneğin:

```java
class Person {
    String name;
    Person(String name) { this.name = name; }

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;
        if (obj == null || getClass() != obj.getClass()) return false;
        Person p = (Person) obj;
        return name.equals(p.name);
    }
}
```

Artık `new Person("Ali")` ile `new Person("Ali")` **eşit** kabul edilir.

---

### 133) `hashCode()` neden override edilir?

Java’daki **hash tabanlı koleksiyonlar** (`HashMap`, `HashSet`, `Hashtable`) hem `equals()` hem `hashCode()` metodunu kullanır.

Kural:

- Eğer iki nesne `equals()` açısından eşitse → `hashCode()` değerleri de **aynı olmalı**.
    
- Tersi gerekmez.
    

Aksi durumda `HashSet`’e aynı nesneyi iki kere ekleyebilirsin — yanlış davranış olur.

---

### 134) `equals()` ve `hashCode()` ilişkisi

Java standardına göre:

1. `x.equals(y)` → `true` ise, `x.hashCode() == y.hashCode()` olmalı.
    
2. `x.equals(y)` → `false` olsa bile, hash’leri **aynı olabilir** (çakışma).
    
3. Hash kodu değişmemelidir (immutable veriye dayanmalı).
    

Bu kurallar `HashMap` ve `HashSet`’in doğru çalışması için zorunludur.

---

### 135) `toString()` metodu nedir?

Bir nesnenin **okunabilir temsilini** döndürür.  
Varsayılan hali:

```java
className@hexHashCode
```

Örnek:

```java
Person p = new Person("Ali");
System.out.println(p.toString());
```

Çıktı: `Person@5ca881b5`

Genelde override edilir:

```java
@Override
public String toString() {
    return "Person{name='" + name + "'}";
}
```

---

### 136) `getClass()` metodu nedir?

Bir nesnenin **runtime sınıf bilgisini** döndürür.  
Bu, **reflection (yansıma)** mekanizmasının temelidir.

```java
Car c = new Car();
System.out.println(c.getClass().getName()); // Car
```

Dönüş tipi: `Class<?>`  
Bu bilgi, dinamik nesne oluşturma (`Class.forName()`, `newInstance()`) gibi işlemlerde kullanılır.

---

### 137) `clone()` metodu nedir?

Bir nesnenin **kopyasını oluşturur**.  
`Object.clone()` **shallow copy (yüzeysel kopya)** yapar.

Kullanmak için:

1. Sınıf `Cloneable` arayüzünü implemente etmeli.
    
2. `clone()` metodunu override etmelisin.
    

```java
class Person implements Cloneable {
    int age;
    public Person clone() throws CloneNotSupportedException {
        return (Person) super.clone();
    }
}
```

Aksi halde `CloneNotSupportedException` fırlatılır.

---

### 138) Shallow copy ve Deep copy farkı nedir?

**Shallow copy:**

- Sadece nesnenin **referanslarını** kopyalar.
    
- Alt nesneler **aynı referansı** paylaşır.
    

**Deep copy:**

- Alt nesneler dahil **tam bir kopya** oluşturur.
    
- Her şey bağımsız olur.
    

```java
Person p1 = new Person(new Address("İzmir"));
Person p2 = (Person) p1.clone(); // shallow copy
```

`p1.address` ve `p2.address` aynı nesneyi gösterir.  
Deep copy yaparsan, `Address` de klonlanır.

---

### 139) `finalize()` metodu `Object` sınıfında mı tanımlıdır?

Evet.  
`Object` içinde `protected void finalize()` olarak tanımlıdır.  
Garbage collector bir nesneyi temizlemeden önce çağırır.

Ancak Java 9’dan itibaren **kullanımı yasaklanmıştır** (`deprecated`).  
Yerine `AutoCloseable` veya `Cleaner` sınıfları kullanılmalı.

---

### 140) `wait()`, `notify()`, `notifyAll()` metotları `Object`’te neden tanımlıdır?

Çünkü her nesne bir **monitor lock** (kilit mekanizması) taşır.  
Bu metotlar, thread’lerin o kilit üzerinden haberleşmesini sağlar.

Yani yalnızca thread değil, **her nesne** senkronizasyon noktasına dönüşebilir.  
Bu yüzden `Thread` sınıfında değil, `Object`’te tanımlıdır.

---

### 141) Java Collections Framework nedir?

Java Collections Framework (JCF), **veri kümelerini (collections)** depolamak, erişmek ve yönetmek için oluşturulmuş sınıflar ve arayüzler setidir.

Temel arayüzler:

- `Collection`
    
    - `List`
        
    - `Set`
        
    - `Queue`
        
- `Map` (Collection’ın parçası değildir ama benzer davranır)
    

Avantajları:

- Kod tekrarını azaltır.
    
- Veri yapılarının (list, set, map) ortak davranışlarını standartlaştırır.
    
- Algoritma sınıfları (`Collections`, `Arrays`) ile kolay manipülasyon sağlar.
    

---

### 142) `List`, `Set` ve `Map` farkı nedir?

|Özellik|`List`|`Set`|`Map`|
|---|---|---|---|
|Eleman sırası|Korumalıdır|Rastgele veya sıralı|Anahtar-değer çifti|
|Tekrarlayan eleman|Olabilir|Olamaz|Anahtarlar benzersiz|
|Erişim yöntemi|Index|Eleman|Key|
|Örnek sınıflar|`ArrayList`, `LinkedList`|`HashSet`, `TreeSet`|`HashMap`, `TreeMap`|

---

### 143) `ArrayList` ve `LinkedList` farkı nedir?

|Özellik|`ArrayList`|`LinkedList`|
|---|---|---|
|Yapı|Dinamik dizi|Çift bağlı liste|
|Erişim süresi|O(1) (index ile hızlı)|O(n)|
|Ekleme/silme|Yavaş (veri kaydırma gerekir)|Hızlı (referans güncellenir)|
|Bellek kullanımı|Daha az|Daha fazla (referanslar tutulur)|
|Kullanım|Sık erişim|Sık ekleme/silme|

Yani:

- **Okuma ağırlıklı** → `ArrayList`
    
- **Yazma ağırlıklı** → `LinkedList`
    

---

### 144) `HashSet` ve `TreeSet` farkı nedir?

|Özellik|`HashSet`|`TreeSet`|
|---|---|---|
|Sıra|Rastgele|Artan sırada|
|Performans|Daha hızlı (O(1))|Daha yavaş (O(log n))|
|Null|1 tane olabilir|Null kabul etmez|
|Uygulama|HashMap tabanlı|TreeMap tabanlı|

`HashSet` hız için, `TreeSet` sıralı veri için kullanılır.

---

### 145) `HashMap` ve `Hashtable` farkı nedir?

|Özellik|`HashMap`|`Hashtable`|
|---|---|---|
|Senkronizasyon|Hayır (thread-safe değil)|Evet (synchronized)|
|Null key/value|Evet (1 key, birçok value)|Hayır|
|Performans|Daha hızlı|Daha yavaş|
|Tanıtıldığı sürüm|Java 1.2|Java 1.0|

Modern uygulamalarda `HashMap` tercih edilir.  
Çoklu thread ortamında `ConcurrentHashMap` kullanmak daha doğrudur.

---

### 146) `HashMap`’te anahtarlar (keys) nasıl saklanır?

`HashMap` anahtarları **hashing algoritması** kullanarak saklar.  
Her key için `hashCode()` çağrılır, sonra bu değer tablo boyutuna göre bir **index’e** dönüştürülür.  
Çakışma olursa (`hash collision`), aynı “bucket” içinde **linked list** (Java 8’den itibaren gerekirse tree) olarak tutulur.

Yani:  
`hash(key)` → `index` → `bucket` → `entry(key, value)`

---

### 147) `fail-fast` iterator nedir?

Bir koleksiyon üzerinde `Iterator` ile dolaşırken, koleksiyon **yapısal olarak değiştirilirse**, iterator `ConcurrentModificationException` fırlatır.

Örnek:

```java
List<Integer> list = new ArrayList<>();
list.add(1);
Iterator<Integer> it = list.iterator();
list.add(2); // değişiklik
it.next();   // hata!
```

Bu davranışa **fail-fast** denir.  
Çözüm: `Iterator.remove()` kullanmak veya `CopyOnWriteArrayList` gibi eşzamanlı koleksiyonlar.

---

### 148) `Iterator` ve `ListIterator` farkı nedir?

|Özellik|`Iterator`|`ListIterator`|
|---|---|---|
|Erişim yönü|Tek yönlü|Çift yönlü|
|Koleksiyon türü|Tüm koleksiyonlar|Sadece `List`|
|Eleman ekleme|Hayır|`add()` ile evet|
|Başlangıç pozisyonu|0’dan başlar|Belirli index’ten başlayabilir|

`ListIterator` ile `previous()` kullanarak geriye doğru da gezebilirsin.

---

### 149) `Comparable` ve `Comparator` farkı nedir?

|Özellik|`Comparable`|`Comparator`|
|---|---|---|
|Arayüzün metodu|`compareTo(Object o)`|`compare(Object o1, Object o2)`|
|Nerede uygulanır|Doğrudan sınıfın içinde|Ayrı bir sınıfta|
|Sıralama türü|Doğal (natural) sıralama|Özel sıralama|
|Örnek|`String`, `Integer` (default)|Özel kriterle (`Comparator.comparing()`)|

**Kural:**

- `Comparable` → tek standart sıralama
    
- `Comparator` → alternatif sıralama
    

---

### 150) `Collections` sınıfı nedir?

`java.util.Collections`, koleksiyonlar üzerinde **yardımcı metotlar (utility methods)** sağlayan **final** bir sınıftır.

Örnek metotlar:

```java
Collections.sort(list);
Collections.reverse(list);
Collections.shuffle(list);
Collections.max(list);
Collections.synchronizedList(list);
```

Yani “koleksiyonlar için statik yardımcı metotlar kütüphanesi”dir.

---

### 151) `Map.Entry` nedir?

`Map.Entry` bir **iç arayüz (inner interface)** olup, bir `Map` içindeki **key–value (anahtar-değer)** çiftini temsil eder.

Örnek kullanım:

```java
Map<String, Integer> map = new HashMap<>();
map.put("Ali", 30);
map.put("Ayşe", 25);

for (Map.Entry<String, Integer> e : map.entrySet()) {
    System.out.println(e.getKey() + " -> " + e.getValue());
}
```

Avantajı: Hem anahtara hem değere doğrudan erişim sağlar.

---

### 152) `Properties` sınıfı nedir?

`Properties`, `Hashtable`’dan türetilmiş bir sınıftır ve **konfigürasyon verilerini** (anahtar–değer çiftlerini) tutmak için kullanılır.  
Anahtar ve değerler **her zaman `String` tipindedir**.

Kullanımı:

```java
Properties p = new Properties();
p.setProperty("user", "burak");
p.setProperty("language", "tr");

System.out.println(p.getProperty("user"));
```

Ayrıca `.properties` dosyalarından veri okumak/yazmak için kullanılır:

```java
p.load(new FileReader("config.properties"));
p.store(new FileWriter("config.properties"), "Config File");
```

---

### 153) `Enumeration` nedir?

`Enumeration`, eski Java sürümlerinde (JDK 1.0) kullanılan **iterator’ın atasıdır**.  
Bugün hala bazı eski sınıflarda (`Vector`, `Hashtable`) kullanılır.

Örnek:

```java
Vector<String> v = new Vector<>();
v.add("A"); v.add("B");
Enumeration<String> e = v.elements();

while (e.hasMoreElements()) {
    System.out.println(e.nextElement());
}
```

Modern alternatif: **`Iterator` veya `for-each`** kullanmak.

---

### 154) `Enum` nedir?

`Enum`, sabit değerlerin **tür güvenli (type-safe)** biçimde tanımlanmasını sağlayan özel bir sınıf türüdür.  
Her `enum` değeri aslında bir **nesnedir**.

```java
enum Gun {
    PAZARTESI, SALI, CARSAMBA, PERSEMBE, CUMA, CUMARTESI, PAZAR
}
Gun g = Gun.PAZARTESI;
```

`enum` içinde metot da tanımlanabilir.  
Örneğin:

```java
enum Seviye {
    DUSUK(1), ORTA(2), YUKSEK(3);
    int kod;
    Seviye(int k) { this.kod = k; }
}
```

---

### 155) `EnumSet` nedir?

`EnumSet`, sadece `enum` tipleriyle çalışan **yüksek performanslı bir Set** implementasyonudur.  
Normal `HashSet`’ten çok daha hızlıdır çünkü bit tabanlı çalışır.

Örnek:

```java
EnumSet<Gun> hafta = EnumSet.of(Gun.PAZARTESI, Gun.CUMA);
```

Sıralama, `enum` tanımlama sırasına göredir.  
Thread-safe değildir, ama `Collections.synchronizedSet()` ile yapılabilir.

---

### 156) Generics (jenerikler) nedir?

Generics, Java’da sınıf ve metotların **tür bağımsız (type-safe)** yazılmasını sağlar.  
Yani “her türle çalışan ama tip güvenli” yapılar oluşturur.

```java
List<String> isimler = new ArrayList<>();
isimler.add("Burak");
String ad = isimler.get(0); // cast gerekmez
```

Avantajları:

- **Compile-time tip güvenliği**
    
- **Casting ihtiyacını ortadan kaldırır**
    
- **Kod tekrarını azaltır**
    

---

### 157) Wildcard (`?`) nedir?

Wildcard (`?`), **bilinmeyen bir türü** temsil eder.  
Üç türü vardır:

1. `?` — herhangi bir tür
    
2. `? extends T` — T veya onun alt türleri
    
3. `? super T` — T veya onun üst türleri
    

Örnek:

```java
List<? extends Number> sayilar = new ArrayList<Integer>();
List<? super Integer> tamSayilar = new ArrayList<Number>();
```

Kural hatırlatması:

> **“extends → okuma, super → yazma”**  
> Yani `extends` ile listeye ekleyemezsin, ama `super` ile ekleyebilirsin.

---

### 158) Bounded type parameters nedir?

Bir generic parametreye sınır koymak demektir.  
Yani sadece belirli türlerin kabul edilmesini sağlar.

```java
class Kutu<T extends Number> {
    T deger;
}
```

Bu sınıf sadece `Integer`, `Float`, `Double` gibi `Number` alt sınıflarıyla çalışır.  
Bu sayede generic kod içinde `Number` metotları (örneğin `doubleValue()`) kullanılabilir.

---

### 159) Generic method nedir?

Bir metodun kendi tür parametresine sahip olmasıdır.  
Sınıf generic olmasa bile metot olabilir.

```java
public <T> void yazdir(T veri) {
    System.out.println(veri);
}
```

Çağrıldığında tip otomatik belirlenir:

```java
yazdir("Merhaba");
yazdir(42);
```

Bu sayede aynı metod, farklı türlerle çalışabilir.

---

### 160) `Comparable` ve `Comparator` arasındaki ilişki nedir?

- `Comparable`, bir sınıfın **kendi doğal sıralama mantığını** belirtir.
    
- `Comparator`, **harici (external)** bir sıralama mantığı tanımlar.
    

Bir sınıf aynı anda `Comparable`’ı implemente edip, alternatif sıralama için `Comparator` nesneleriyle de kullanılabilir.

Örnek:

```java
class Kisi implements Comparable<Kisi> {
    int yas;
    public int compareTo(Kisi k) {
        return this.yas - k.yas;
    }
}
```

Alternatif sıralama:

```java
Comparator<Kisi> isimSirasi = (a, b) -> a.isim.compareTo(b.isim);
```

---

### 161) Java I/O (Input/Output) nedir?

Java I/O, **veri giriş/çıkışı (input/output)** işlemlerini yapan sınıflar bütünüdür.  
Dosya okuma, yazma, ağdan veri alma veya terminale çıktı verme bu sistemle yapılır.

I/O yapısı iki temel hiyerarşiye ayrılır:

- **Byte stream** (bayt bazlı): `InputStream`, `OutputStream`
    
- **Character stream** (karakter bazlı): `Reader`, `Writer`
    

---

### 162) Byte stream ve Character stream farkı nedir?

|Özellik|Byte Stream|Character Stream|
|---|---|---|
|Temel sınıf|`InputStream`, `OutputStream`|`Reader`, `Writer`|
|Veri tipi|8-bit byte|16-bit Unicode karakter|
|Kullanım|Görsel, ses, PDF gibi binary dosyalar|Metin dosyaları|
|Örnek|`FileInputStream`, `BufferedOutputStream`|`FileReader`, `BufferedWriter`|

**Özet:**  
Binary dosya → byte stream  
Text dosya → character stream

---

### 163) `File` sınıfı nedir?

`java.io.File`, dosya veya dizinleri temsil eden bir sınıftır.  
Dosyanın **var olup olmadığını, boyutunu, adını** kontrol edebilirsin ama içeriğini **okumaz/yazmaz**.

Örnek:

```java
File f = new File("data.txt");
if (f.exists()) {
    System.out.println("Boyut: " + f.length());
}
```

`File` sadece **dosya sistemini temsil eder**, I/O akışı sağlamaz.

---

### 164) `FileReader` ve `FileWriter` nedir?

Bunlar **character stream** sınıflarıdır.

- `FileReader` → dosyadan karakter okur.
    
- `FileWriter` → dosyaya karakter yazar.
    

Örnek:

```java
FileWriter fw = new FileWriter("dosya.txt");
fw.write("Merhaba Java");
fw.close();
```

Büyük dosyalarda `BufferedReader` / `BufferedWriter` ile birlikte kullanmak performansı artırır.

---

### 165) `FileInputStream` ve `FileOutputStream` farkı nedir?

Bunlar **byte stream** sınıflarıdır.  
Yani veriyi byte byte okur/yazar (metin değil, binary düzeyde).

```java
FileInputStream in = new FileInputStream("image.jpg");
FileOutputStream out = new FileOutputStream("copy.jpg");

int i;
while ((i = in.read()) != -1)
    out.write(i);

in.close();
out.close();
```

Görsel, ses, PDF gibi binary dosyalar için kullanılır.

---

### 166) `BufferedReader` nedir?

`BufferedReader`, karakterleri **bellekte tamponlayarak (buffer)** okur.  
Bu sayede okuma işlemleri çok daha hızlı olur.

```java
BufferedReader br = new BufferedReader(new FileReader("metin.txt"));
String satir;
while ((satir = br.readLine()) != null) {
    System.out.println(satir);
}
br.close();
```

Avantajı: Satır satır okuma (`readLine()`) sağlar ve I/O işlemini minimize eder.

---

### 167) Serialization (serileştirme) nedir?

Bir nesnenin durumunu (state) **bayt dizisine dönüştürüp** diske yazmak veya ağdan göndermek işlemidir.

Java’da bunun için `Serializable` arayüzü kullanılır:

```java
class Person implements Serializable {
    String name;
    int age;
}
```

Yazmak:

```java
ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream("p.ser"));
oos.writeObject(new Person("Burak", 30));
oos.close();
```

Okumak:

```java
ObjectInputStream ois = new ObjectInputStream(new FileInputStream("p.ser"));
Person p = (Person) ois.readObject();
```

---

### 168) Deserialization (ters serileştirme) nedir?

Serileştirilmiş bir nesnenin, **bayt dizisinden tekrar nesneye dönüştürülmesidir**.  
Yani `ObjectInputStream` kullanarak okunan veri, yeniden Java nesnesine çevrilir.

```java
ObjectInputStream in = new ObjectInputStream(new FileInputStream("data.ser"));
Person p = (Person) in.readObject();
```

Serialization ve deserialization **aynı `serialVersionUID`** değeriyle çalışmalıdır.

---

### 169) `transient` anahtar kelimesi nedir?

Bir sınıf serileştirilirken, **bazı alanların kaydedilmemesini** sağlar.  
Yani `transient` olarak işaretlenen alanlar **serialization sırasında yok sayılır.**

```java
class User implements Serializable {
    String username;
    transient String password;
}
```

`password` diske yazılmaz — güvenlik için kullanılır.

---

### 170) `serialVersionUID` nedir?

Serileştirilen sınıflar için **benzersiz bir kimlik numarasıdır.**  
Serialization sırasında, okunan nesne ile sınıfın sürümü uyuşmazsa hata alınır.

```java
private static final long serialVersionUID = 1L;
```

Eğer bunu elle belirtmezsen, JVM otomatik oluşturur — ama sınıfta bir değişiklik yaparsan **uyumsuzluk (InvalidClassException)** oluşabilir.  
Bu yüzden, `serialVersionUID` **manuel tanımlanmalıdır.**

---

### 171) Lambda expression nedir?

Lambda, Java 8 ile gelen **anonim fonksiyon** yazma biçimidir.  
Yani “ismi olmayan metot”.  
Daha kısa, fonksiyonel kod yazmayı sağlar.

Örnek:

```java
// klasik
Runnable r = new Runnable() {
    public void run() { System.out.println("Çalıştı!"); }
};

// lambda ile
Runnable r2 = () -> System.out.println("Çalıştı!");
```

Kural: Lambda sadece **functional interface**’lerle (tek metot içeren arayüzler) kullanılabilir.  
Örnek: `Runnable`, `Comparator`, `Predicate`, `Function`, `Consumer`.

---

### 172) Functional Interface nedir?

Functional interface, yalnızca **bir tane abstract metodu** olan arayüzdür.  
Java 8’de bu tür arayüzler `@FunctionalInterface` anotasyonu ile işaretlenir.

```java
@FunctionalInterface
interface Hesaplama {
    int topla(int a, int b);
}
```

Kullanımı:

```java
Hesaplama h = (x, y) -> x + y;
System.out.println(h.topla(3, 5));
```

Bunlar **Spring’in @FunctionalBean**, **Reactor’ın Mono/Flux map/filter** fonksiyonlarının arkasındaki temel yapıdır.

---

### 173) Java’nın built-in functional interface’leri nelerdir?

|Interface|Metot|Açıklama|Örnek|
|---|---|---|---|
|`Predicate<T>`|`boolean test(T t)`|Koşul kontrolü|`x -> x > 10`|
|`Function<T,R>`|`R apply(T t)`|Dönüşüm|`x -> x * 2`|
|`Consumer<T>`|`void accept(T t)`|İşlem yapar|`System.out::println`|
|`Supplier<T>`|`T get()`|Değer üretir|`() -> Math.random()`|
|`BiFunction<T,U,R>`|`R apply(T,U)`|2 parametreli fonksiyon|`(a,b)->a+b`|

Spring Stream, Reactor, Optional API’lerinde hepsi bolca geçer.

---

### 174) Method Reference nedir?

Lambda ifadelerinin sadeleştirilmiş halidir.  
Yani “hazır metodu lambda yerine geçir”.

Örnek:

```java
list.forEach(System.out::println);
```

Aynısı:

```java
list.forEach(x -> System.out.println(x));
```

Kullanım tipleri:

- `Class::staticMethod`
    
- `instance::instanceMethod`
    
- `Class::new` (constructor reference)
    

Bu özellikle `Collectors`, `map`, `filter` gibi Stream çağrılarında çok sık görülür.

---

### 175) Stream API nedir?

Stream, koleksiyonlar üzerinde **veri işleme boru hattıdır (data pipeline)**.  
Java 8’de geldi, functional yaklaşımı destekler.

Örnek:

```java
List<Integer> sayilar = Arrays.asList(1,2,3,4,5);
sayilar.stream()
       .filter(x -> x % 2 == 0)
       .map(x -> x * 2)
       .forEach(System.out::println);
```

Stream = **kaynak → ara işlemler → terminal işlem.**

---

### 176) Intermediate (ara) ve Terminal işlemler farkı nedir?

**Intermediate (ara işlemler):**  
Veriyi dönüştürür, stream döndürür. Lazy evaluation (tembel hesaplama).  
Örnek: `filter()`, `map()`, `sorted()`, `distinct()`.

**Terminal işlemler:**  
Stream’i bitirir, sonuç döndürür.  
Örnek: `forEach()`, `collect()`, `reduce()`, `count()`.

Stream zinciri, terminal işlem çağrılmadan **hiç çalışmaz**.

---

### 177) `map()` ve `flatMap()` farkı nedir?

- `map()` → her elemanı **tek değer**e dönüştürür.
    
- `flatMap()` → her elemanı **birden fazla değeri içeren stream**’e dönüştürür, sonra düzleştirir.
    

```java
List<List<Integer>> sayilar = Arrays.asList(Arrays.asList(1,2), Arrays.asList(3,4));
sayilar.stream()
       .flatMap(List::stream)
       .forEach(System.out::println);
```

Çıktı: `1 2 3 4`  
Yani nested (iç içe) yapı → düzleştirilmiş liste.

---

### 178) Optional nedir?

`Optional<T>` null kontrollerini güvenli hale getiren bir kapsayıcı sınıftır.  
NullPointerException düşürmeden veriyle çalışmamızı sağlar.

```java
Optional<String> isim = Optional.ofNullable(getName());
isim.ifPresent(System.out::println);
```

Ana metotlar:

- `of()`, `ofNullable()`
    
- `isPresent()`, `ifPresent()`
    
- `orElse()`, `orElseGet()`
    
- `map()`, `flatMap()`
    

Spring Data metot dönüşlerinde (`findById()`, `findFirstBy...`) sıklıkla kullanılır.

---

### 179) Parallel Stream nedir?

Stream işlemlerini **çok çekirdekli CPU**’larda paralel çalıştırır.  
Yani her işlem farklı thread üzerinde yürütülür.

```java
list.parallelStream().forEach(System.out::println);
```

Avantaj: Büyük veri setlerinde hız.  
Dezavantaj: Sıralama garantisi yok, thread overhead’i olabilir.  
Dikkat: Stateless (yan etkisiz) fonksiyonlarla kullanılmalı.

---

### 180) Collectors API nedir?

Stream sonuçlarını koleksiyonlara, istatistiklere veya özel yapılara dönüştürür.

Örnekler:

```java
// Listeye dönüştürme
List<Integer> ciftler = sayilar.stream()
    .filter(x -> x % 2 == 0)
    .collect(Collectors.toList());

// Gruplama
Map<String, List<Employee>> byDept =
    employees.stream().collect(Collectors.groupingBy(Employee::getDepartment));
```

Spring Boot projelerinde `Collectors.groupingBy`, `mapping`, `joining` gibi işlemler genellikle DTO dönüştürürken veya raporlama için çok kullanılır.

---

### 181) `ExecutorService` nedir?

`ExecutorService`, thread oluşturma işini manuel yapmadan yönetmek için kullanılan bir **thread pool yöneticisidir.**  
Her `new Thread()` açmak pahalıdır, o yüzden havuz mantığı kullanılır.

Örnek:

```java
ExecutorService executor = Executors.newFixedThreadPool(4);
executor.submit(() -> System.out.println("İş çalıştı"));
executor.shutdown();
```

Avantaj:

- Thread havuzunu otomatik yönetir.
    
- Paralel görevleri sıraya alır.
    
- Spring’in `@Async`, `TaskExecutor` ve `ThreadPoolTaskExecutor`’larının temeli budur.
    

---

### 182) `Callable` ve `Runnable` farkı nedir?

|Özellik|Runnable|Callable|
|---|---|---|
|Dönüş değeri|Yok (`void`)|Var (`T`)|
|Exception fırlatabilir mi|Hayır|Evet (`throws Exception`)|
|Metot adı|`run()`|`call()`|
|Kullanıldığı yer|`Thread`, `ExecutorService`|`ExecutorService`|

Örnek:

```java
Callable<Integer> task = () -> 5 + 10;
Future<Integer> f = executor.submit(task);
System.out.println(f.get());
```

`Callable` → thread sonuç döndüren versiyon.

---

### 183) `Future` nedir?

`Future`, bir asenkron görevin sonucunu **ileride** almayı sağlar.

```java
Future<Integer> future = executor.submit(() -> 42);
System.out.println(future.get()); // bloklar
```

Yani `get()` çağrılana kadar thread devam eder, `get()` sonucu bekler.

Dezavantaj: `Future` sonuç hazır değilse **bloklar** → bu yüzden `CompletableFuture` geldi.

---

### 184) `CompletableFuture` nedir?

`CompletableFuture`, asenkron işlemleri **non-blocking** (beklemeden) şekilde zincirlemeni sağlar.  
Yani “promise/future chaining”.

```java
CompletableFuture.supplyAsync(() -> getUser())
    .thenApply(user -> enrich(user))
    .thenAccept(System.out::println);
```

Artık `get()` ile beklemek zorunda değilsin, callback zinciriyle ilerlersin.  
Spring WebFlux, Reactor, Project Loom bu yapının üstüne inşa edilmiştir.

---

### 185) `CompletableFuture` ile exception handling nasıl yapılır?

Her zincir `exceptionally()` veya `handle()` metodu ile hataları yönetebilir.

```java
CompletableFuture.supplyAsync(() -> riskyCall())
    .exceptionally(ex -> {
        System.out.println("Hata: " + ex.getMessage());
        return "varsayılan";
    })
    .thenAccept(System.out::println);
```

Böylece try-catch yerine fonksiyonel hata yönetimi yapılır.

---

### 186) `synchronized` blok yerine hangi modern yapılar kullanılır?

Manuel `synchronized` yerine **java.util.concurrent.locks** paketindeki araçlar tercih edilir:

- `ReentrantLock` → kilit üzerinde daha fazla kontrol sağlar.
    
- `ReadWriteLock` → okuma/yazma ayrı kilitlenir.
    
- `Semaphore` → kaynak sayısını kontrol eder.
    
- `CountDownLatch`, `CyclicBarrier` → thread senkronizasyonu sağlar.
    
- `AtomicInteger`, `ConcurrentHashMap` → lock-free concurrency.
    

Spring Boot’un `@Scheduled`, `@Async` görevleri bu yapıların üst düzey soyutlamasıdır.

---

### 187) `CountDownLatch` nedir?

Bir grup thread’in **belirli bir koşulu beklemesini** sağlar.  
Yani bir sayaç sıfıra inene kadar diğer thread’ler bekler.

```java
CountDownLatch latch = new CountDownLatch(3);
for (int i = 0; i < 3; i++) {
    new Thread(() -> { task(); latch.countDown(); }).start();
}
latch.await(); // hepsi bitene kadar bekler
System.out.println("Tüm işler tamam!");
```

Kullanım yeri: test senkronizasyonu, batch işlemleri.

---

### 188) `CyclicBarrier` nedir?

`CountDownLatch`’e benzer ama **tekrarlanabilir** (barrier yeniden kullanılabilir).  
Tüm thread’ler bariyere ulaştığında aynı anda devam ederler.

```java
CyclicBarrier barrier = new CyclicBarrier(3, () -> System.out.println("Bariyer aşıldı!"));
for (int i = 0; i < 3; i++) {
    new Thread(() -> {
        awaitTask();
        barrier.await();
    }).start();
}
```

Kullanım: Aynı anda başlayacak paralel hesaplamalar.

---

### 189) `Semaphore` nedir?

Belirli sayıda thread’in aynı anda bir kaynağa erişmesini sağlar.  
Yani “izin sistemi”.

```java
Semaphore sem = new Semaphore(2); // aynı anda 2 izin
for (int i = 0; i < 5; i++) {
    new Thread(() -> {
        try {
            sem.acquire();
            System.out.println(Thread.currentThread().getName() + " çalışıyor");
            Thread.sleep(1000);
            sem.release();
        } catch (Exception ignored) {}
    }).start();
}
```

Bu sistem thread sayısını veya eşzamanlı kaynak erişimini kontrol eder.

---

### 190) `ConcurrentHashMap` nedir?

`HashMap`’in thread-safe (çoklu erişim güvenli) versiyonudur.  
Klasik `HashMap` eşzamanlı kullanıldığında `ConcurrentModificationException` fırlatır.  
`ConcurrentHashMap` bunu **segment-based locking** (bölgesel kilitleme) ile çözer.

```java
ConcurrentHashMap<String, Integer> map = new ConcurrentHashMap<>();
map.put("A", 1);
map.computeIfAbsent("B", k -> 2);
```

Spring Cache, Spring Security Session Store ve hatta bazı Redis client’ları bu yapıyı içeride kullanır.

---

### 191) `map()` ve `filter()` zincirinde `Optional` nasıl kullanılır?

`Optional` içinde fonksiyonel işlemler yapılabilir, null kontrolü gerekmez.

```java
Optional<String> isim = Optional.of("burak");

isim.filter(s -> s.length() > 3)
    .map(String::toUpperCase)
    .ifPresent(System.out::println);
```

Burada `filter` koşul tutmazsa zincir durur, `map` çağrılmaz.  
Bu `Optional`’ı mini bir Stream gibi kullanmamızı sağlar.  
Spring Data’da `findById()` dönen `Optional` için çok kullanılır.

---

### 192) `Collectors.groupingBy()` nedir?

Stream sonuçlarını bir özelliğe göre **gruplar**.  
SQL’deki `GROUP BY` gibidir.

```java
Map<String, List<Employee>> byDept = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDepartment));
```

İkinci argümanla alt işlemler de eklenebilir:

```java
Map<String, Long> sayi = employees.stream()
    .collect(Collectors.groupingBy(Employee::getDepartment, Collectors.counting()));
```

Spring Boot servis katmanında DTO istatistikleri oluşturmakta sık kullanılır.

---

### 193) `partitioningBy()` nedir?

`groupingBy`’un boolean versiyonudur.  
Stream’i ikiye ayırır: koşulu sağlayanlar ve sağlamayanlar.

```java
Map<Boolean, List<Integer>> sonuc =
    sayilar.stream().collect(Collectors.partitioningBy(x -> x % 2 == 0));
```

Çıktı:

```
true -> [2,4,6]
false -> [1,3,5]
```

Böylece filter yerine iki yönlü ayrım yapılır.

---

### 194) `joining()` nedir?

String stream’lerini tek bir String’e birleştirir.

```java
String adlar = employees.stream()
    .map(Employee::getName)
    .collect(Collectors.joining(", "));
System.out.println(adlar); // "Ali, Ayşe, Burak"
```

DTO’ları loglama, e-posta listesi veya CSV üretimi için mükemmeldir.

---

### 195) `reduce()` nedir?

Tüm elemanları **tek bir sonuca indirger.**  
Toplama, çarpma, maksimum/minimum bulma gibi işlemlerde kullanılır.

```java
int toplam = sayilar.stream().reduce(0, Integer::sum);
```

`reduce` → bir Stream’de “aggregate” işlemi yapar.  
Spring Data Projection’lar veya custom query sonuçlarında çok kullanışlı.

---

### 196) `record` nedir? _(Java 16+)_

`record`, veri taşıyan sınıflar (DTO’lar) için **otomatik getter, equals, hashCode, toString** üreten yeni bir sınıf tipidir.

```java
public record UserDto(String name, int age) {}
```

Otomatik olarak immutable’dır.  
Spring Boot’ta request/response DTO’larında mükemmel:

```java
record LoginRequest(String username, String password) {}
```

Yani “Lombok’suz data class”.

---

### 197) `sealed class` nedir? _(Java 17+)_

Sınıfın hangi alt sınıflar tarafından genişletilebileceğini **kısıtlar.**

```java
public sealed class Payment permits CreditCard, Cash {}
public final class CreditCard extends Payment {}
public final class Cash extends Payment {}
```

Bu yapı `enum` kadar katı değildir ama miras zincirini kontrol eder.  
Spring Security ve domain model’lerde type-safety için çok işe yarar.

---

### 198) Pattern Matching for `instanceof` nedir? _(Java 14+)_

Eskiden:

```java
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.toUpperCase());
}
```

Artık:

```java
if (obj instanceof String s) {
    System.out.println(s.toUpperCase());
}
```

Tip dönüşümü otomatik olur, kod sadeleşir.  
Spring AOP veya Reflection tabanlı kodlarda tip kontrolü için kullanışlı.

---

### 199) Switch Expressions _(Java 14+)_

Yeni switch ifadesi artık **değer döndürür** ve ok syntax’ı kullanır.

```java
String gunTipi = switch (gun) {
    case MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY -> "Hafta içi";
    case SATURDAY, SUNDAY -> "Hafta sonu";
};
```

Yani `switch` artık expression gibi davranıyor.  
Spring Enum mapping veya status handling için çok uygun.

---

### 200) `var` anahtar kelimesi nedir? _(Java 10+)_

`var`, derleyicinin değişken tipini **otomatik çıkarmasını** sağlar.  
Type inference (tür çıkarımı) yapar.

```java
var list = new ArrayList<String>(); // tür: ArrayList<String>
var sayi = 10;                      // tür: int
```

Avantaj: gereksiz tekrar azalır, kod sadeleşir.  
Dezavantaj: tip belirsizse okunabilirlik düşer.  
Spring Boot config’lerde, builder pattern’lerde sıkça tercih edilir.

---

### 201) `java.time` API’si nedir?

Java 8 ile gelen **modern tarih ve zaman API’si**’dir.  
Eski `Date` ve `Calendar` sınıflarının tüm saçmalıklarını çözer.  
Immutable’dır, thread-safe’tir, ve `java.time` paketindedir.

Temel sınıflar:

- `LocalDate` → sadece tarih (2025-10-08)
    
- `LocalTime` → sadece saat (14:32:10)
    
- `LocalDateTime` → tarih + saat
    
- `Instant` → UTC tabanlı zaman damgası
    
- `ZonedDateTime` → timezone içeren tarih-saat
    

Bu API, Spring Boot’un `@DateTimeFormat`, Jackson `@JsonFormat` anotasyonlarının dayandığı altyapıdır.

---

### 202) `LocalDate`, `LocalTime`, `LocalDateTime` farkı nedir?

|Sınıf|Ne içerir|Örnek|
|---|---|---|
|`LocalDate`|Yıl, ay, gün|`2025-10-08`|
|`LocalTime`|Saat, dakika, saniye|`14:35:42`|
|`LocalDateTime`|Tarih + saat|`2025-10-08T14:35:42`|

Kullanım:

```java
LocalDate d = LocalDate.now();
LocalDateTime dt = LocalDateTime.of(2025, 10, 8, 14, 35);
```

Hepsi immutable’dır. `plusDays()`, `minusHours()` gibi metotlarla manipüle edilir.

---

### 203) `Instant` nedir?

`Instant`, zamanın **UTC (epoch)** bazlı temsili.  
Yani “1970-01-01T00:00:00Z”’dan itibaren geçen saniye/nano sayısı.

```java
Instant now = Instant.now();
System.out.println(now); // 2025-10-08T11:37:00Z
```

`Instant` → **timestamp (UTC)**  
`LocalDateTime` → **bölgesel zaman**  
Spring log’larında, JWT expiration’larda, veritabanı timestamp kolonlarında genelde `Instant` kullanılır.

---

### 204) `ZoneId` ve `ZonedDateTime` nedir?

Zaman dilimi yönetimini sağlar.  
`ZoneId` → zaman dilimini belirtir (`Europe/Istanbul`, `UTC`, `America/New_York`).  
`ZonedDateTime` → `LocalDateTime` + `ZoneId`.

```java
ZonedDateTime zdt = ZonedDateTime.now(ZoneId.of("Europe/Istanbul"));
System.out.println(zdt);
```

Zaman dilimi dönüşümü:

```java
ZonedDateTime utc = zdt.withZoneSameInstant(ZoneId.of("UTC"));
```

Bu, Spring Boot’ta `@JsonFormat(timezone="UTC")` ayarının teknik karşılığıdır.

---

### 205) `Duration` ve `Period` farkı nedir?

|Sınıf|Birimi|Kullanım amacı|
|---|---|---|
|`Duration`|Saat, dakika, saniye|Zaman farkı (Time-based)|
|`Period`|Gün, ay, yıl|Tarih farkı (Date-based)|

```java
Duration d = Duration.between(LocalTime.NOON, LocalTime.now());
Period p = Period.between(LocalDate.of(2024,1,1), LocalDate.now());
```

`Duration` genelde performans ölçümü için;  
`Period` yaş, vade, abonelik süresi hesaplamalarında kullanılır.

---

### 206) `Date` → `LocalDate` dönüşümü nasıl yapılır?

Legacy (`java.util.Date`) API ile modern `java.time` API birlikte kullanılabiliyor.  
Dönüştürme örnekleri:

```java
Date date = new Date();
Instant instant = date.toInstant();
LocalDateTime ldt = instant.atZone(ZoneId.systemDefault()).toLocalDateTime();
```

Tersine:

```java
Date fromLdt = Date.from(ldt.atZone(ZoneId.systemDefault()).toInstant());
```

Spring Boot’ta genelde Jackson otomatik dönüştürür ama mapper (MapStruct, ModelMapper) yazarken bu bilmek şart.

---

### 207) `DateTimeFormatter` nedir?

Tarih/saat biçimlendirmesini sağlar.  
`SimpleDateFormat`’in modern ve thread-safe versiyonudur.

```java
DateTimeFormatter fmt = DateTimeFormatter.ofPattern("dd-MM-yyyy HH:mm");
String formatted = LocalDateTime.now().format(fmt);
```

Ayrıca parse işlemi de yapar:

```java
LocalDate parsed = LocalDate.parse("08-10-2025", fmt);
```

Bu, Spring Boot’ta `@DateTimeFormat(pattern="yyyy-MM-dd")`’in arka plan mekanizmasıdır.

---

### 208) `parallelStream()` performans kazandırır mı?

Cevap: “Bazen evet, bazen hayır.”  
`parallelStream()` Stream’i **çok çekirdekli CPU’larda paralel yürütür**, ama:

- Küçük listelerde overhead zarar verir.
    
- I/O bound işlerde (DB, HTTP) etkisizdir.
    
- CPU-bound işler (matematik, dönüşüm) için faydalıdır.
    

Kural:

> Sadece **stateless** ve **yan etkisiz (pure function)** işlemlerle kullan.

Spring Boot servis katmanında genelde `CompletableFuture` tercih edilir, `parallelStream` değil.

---

### 209) Custom Collector nedir?

Kendi `Collector`’ını yazabilirsin — özel toplama davranışları tanımlamak için.  
Örneğin, Stream sonucu `TreeSet` olarak döndürmek:

```java
Collector<String, ?, TreeSet<String>> toTreeSet =
    Collector.of(TreeSet::new, TreeSet::add, (a,b)->{a.addAll(b); return a;});

TreeSet<String> result = names.stream().collect(toTreeSet);
```

Bu yaklaşım `Collectors.toMap()`’ın davranışını özelleştirmek veya özel DTO gruplama yapmakta çok işe yarar.

---

### 210) `peek()` nedir, ne işe yarar?

`peek()` debugging amaçlı kullanılır — Stream zincirinde ara değerleri görmeni sağlar.

```java
List<Integer> sonuc = sayilar.stream()
    .filter(x -> x > 2)
    .peek(x -> System.out.println("Filtre sonrası: " + x))
    .map(x -> x * 2)
    .toList();
```

`peek()` genellikle loglama/debug içindir, **yan etki yaratmak için değil**.  
Spring Data Stream’lerinde log debug’ı yaparken çok işine yarar.

---

### 211) Reflection API nedir?

Reflection, Java programının **çalışma zamanında (runtime)** kendi sınıflarını, metotlarını, alanlarını incelemesini ve değiştirmesini sağlar.

Kısaca: “Kodun kendini sorgulaması.”

Örnek:

```java
Class<?> clazz = Class.forName("com.example.User");
for (Method m : clazz.getDeclaredMethods()) {
    System.out.println(m.getName());
}
```

Reflection sayesinde Spring:

- Bean’leri bulur (`@Component`, `@Service`)
    
- Anotasyonları okur (`@Autowired`, `@RequestMapping`)
    
- Proxy objeler oluşturur (AOP, Transactional)
    

Ama dikkat: Reflection yavaş ve pahalı bir işlemdir; framework’ler bunu optimize eder.

---

### 212) `Class` nesnesi nedir?

Her Java sınıfının JVM’de bir `Class` nesnesi vardır.  
Bu nesne, sınıfın yapısını temsil eder.

Elde etmenin üç yolu:

```java
Class<?> c1 = String.class;
Class<?> c2 = "test".getClass();
Class<?> c3 = Class.forName("java.lang.String");
```

`Class` nesnesiyle:

- Alanlara (`getDeclaredFields`)
    
- Metotlara (`getDeclaredMethods`)
    
- Constructor’lara (`getDeclaredConstructors`)  
    erişebilirsin.  
    Spring Bean taraması da bu nesneyle yapılır.
    

---

### 213) Reflection ile nesne nasıl oluşturulur?

Reflection kullanarak **new** operatörü olmadan da nesne yaratabilirsin.

```java
Class<?> c = Class.forName("com.example.User");
Object obj = c.getDeclaredConstructor().newInstance();
```

Bu mekanizma Spring’in **Bean instantiation** sürecinin tam kalbidir.  
Spring Container, `@Component` veya `@Bean` tanımlı sınıfları böyle üretir.

---

### 214) Field ve Method erişimi nasıl yapılır?

Reflection ile private alan ve metotlara bile erişebilirsin.

```java
Field f = User.class.getDeclaredField("username");
f.setAccessible(true);
f.set(userObj, "burak");

Method m = User.class.getDeclaredMethod("login");
m.setAccessible(true);
m.invoke(userObj);
```

Spring’in `@Autowired` ile private field’lara bağımlılık enjekte etmesi de tam olarak bu yöntemle yapılır.

---

### 215) Annotation nedir?

Annotation, derleyiciye veya runtime sistemine **meta bilgi** sağlayan özel yapıdır.  
Yani “koda etiket ekleme” yöntemi.

Örnek:

```java
@Service
public class UserService { ... }
```

Annotation’lar:

- Compile-time’da (`@Override`)
    
- Runtime’da (`@Transactional`, `@RestController`)  
    etkili olabilir.
    

Spring Boot’un büyük kısmı annotation temellidir — dependency injection, mapping, AOP vs.

---

### 216) Custom Annotation nasıl oluşturulur?

Kendi annotation’ını tanımlayabilirsin.

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
public @interface Loggable {
    String value() default "DEBUG";
}
```

Kullanımı:

```java
@Loggable("INFO")
public void saveUser() { ... }
```

`RetentionPolicy.RUNTIME` → Reflection ile erişilebilir hale getirir.  
Spring AOP veya custom logging interceptor’ları tam olarak bu prensiple çalışır.

---

### 217) Meta-annotation’lar nedir?

Annotation’ları tanımlayan annotation’lardır (evet, meta seviye).

Örnekler:

- `@Retention` → yaşam süresini belirler (SOURCE, CLASS, RUNTIME)
    
- `@Target` → nerede kullanılabileceğini belirler (FIELD, METHOD, TYPE)
    
- `@Inherited` → alt sınıfların annotation’ı devralmasını sağlar
    
- `@Documented` → javadoc’a eklenmesini sağlar
    

Spring’in `@Service` ve `@RestController`’ı bile meta-annotated yapılardır (örneğin `@Controller` + `@ResponseBody`).

---

### 218) Spring Framework annotation’ları Reflection ile nasıl işler?

Spring, runtime sırasında:

1. Classpath’i tarar (`ClassLoader` + `Reflection`).
    
2. Annotation’ları bulur (`@Component`, `@Configuration`, `@Bean` vs).
    
3. Bu bilgilere göre Bean nesneleri oluşturur ve yönetir.
    

Basitleştirilmiş hali:

```java
for (Class<?> cls : scannedClasses) {
    if (cls.isAnnotationPresent(Component.class)) {
        context.registerBean(cls);
    }
}
```

Yani Spring “büyü” değil, Reflection + Annotation kombinasyonudur.

---

### 219) `@Retention` türleri nelerdir?

|Tür|Açıklama|Kullanım|
|---|---|---|
|`SOURCE`|Sadece derleme sırasında kullanılır|`@Override`, `@SuppressWarnings`|
|`CLASS`|Bytecode’a eklenir ama runtime’da okunmaz|Varsayılan|
|`RUNTIME`|Runtime’da Reflection ile erişilir|`@Autowired`, `@Service`|

Spring Boot’ta neredeyse tüm annotation’lar `RUNTIME` seviyesindedir, çünkü container onları runtime’da işler.

---

### 220) Dependency Injection (DI) nasıl çalışır?

Spring’in DI sistemi tamamen Reflection’a dayanır:

1. Context sınıfları tarar.
    
2. `@Component`, `@Service`, `@Repository` gibi bean’leri bulur.
    
3. Constructor, field veya setter üzerindeki `@Autowired`’ı bulur.
    
4. Reflection ile o alana bean’i **enjekte eder**.
    

Basitleştirilmiş örnek:

```java
for (Field f : beanClass.getDeclaredFields()) {
    if (f.isAnnotationPresent(Autowired.class)) {
        Object dependency = context.getBean(f.getType());
        f.setAccessible(true);
        f.set(beanInstance, dependency);
    }
}
```

Yani DI sihri = Reflection + Annotation + Bean container.

---

### 221) Proxy nedir?

Proxy, bir sınıfın veya nesnenin **araya girilmiş taklididir**.  
Amaç: Gerçek nesneye erişmeden önce/sonra bir davranış eklemektir.

Kısaca:

> “Kodu değiştirmeden davranışını sarmalamak.”

Örnek:

```java
interface Service { void doWork(); }

class ServiceImpl implements Service {
    public void doWork() { System.out.println("Gerçek iş"); }
}

class ServiceProxy implements Service {
    private final Service target;
    ServiceProxy(Service target) { this.target = target; }

    public void doWork() {
        System.out.println("Önce log");
        target.doWork();
        System.out.println("Sonra cleanup");
    }
}
```

Spring AOP tam olarak bunu yapar — ama manuel değil, Reflection ve Dynamic Proxy ile.

---

### 222) Static proxy ve dynamic proxy farkı nedir?

|Özellik|Static Proxy|Dynamic Proxy|
|---|---|---|
|Yazım şekli|Manuel kodlanır|Runtime’da oluşturulur|
|Esneklik|Düşük|Yüksek|
|Kullanım|Küçük sistemlerde|Framework düzeyinde|
|Java desteği|Kendi sınıfın|`java.lang.reflect.Proxy` veya CGLIB|

Spring AOP, **Dynamic Proxy (JDK Proxy veya CGLIB)** kullanır.  
Statik proxy artık tarih öncesi, ama kavramsal temel hâlâ aynı.

---

### 223) JDK Dynamic Proxy nedir?

`java.lang.reflect.Proxy` sınıfı, runtime’da arayüz tabanlı proxy oluşturur.

```java
Service target = new ServiceImpl();

Service proxy = (Service) Proxy.newProxyInstance(
    target.getClass().getClassLoader(),
    target.getClass().getInterfaces(),
    (p, method, args) -> {
        System.out.println("Before");
        Object result = method.invoke(target, args);
        System.out.println("After");
        return result;
    }
);
proxy.doWork();
```

Yani kodu değiştirmeden “önce/sonra” davranışları eklenebilir.  
Spring, `@Transactional` gibi anotasyonları böyle uygular.

---

### 224) CGLIB nedir?

CGLIB (Code Generation Library), **interface olmayan sınıflar** için dynamic proxy oluşturmayı sağlar.  
Çünkü JDK Proxy sadece interface’lerle çalışır.

Spring otomatik olarak karar verir:

- Bean **bir interface implement ediyorsa** → JDK Proxy
    
- Değilse → CGLIB Proxy
    

CGLIB aslında **sınıfı extend eder** ve metotları override ederek interception sağlar.

---

### 225) AOP (Aspect-Oriented Programming) nedir?

AOP, “cross-cutting concerns” (yani loglama, güvenlik, transaction yönetimi gibi tekrarlanan davranışları) merkezi bir yerde toplama yaklaşımıdır.  
Kısaca:

> Kodun özüne dokunmadan ek davranış enjekte etme.

Spring’te bu şu anlama gelir:  
“Business metotlarına görünmez bir proxy katmanı ekle.”

---

### 226) AOP’nin temel kavramları nelerdir?

|Kavram|Anlamı|
|---|---|
|**Aspect**|Davranışı tanımlayan modül (örnek: LoggingAspect)|
|**Join Point**|Davranışın uygulanabileceği yer (örnek: metot çağrısı)|
|**Advice**|Gerçek eklenen davranış (before/after/around)|
|**Pointcut**|Hangi metotlara uygulanacağını belirten ifade|
|**Weaving**|Aspect’in hedef koda eklenme süreci|

Spring bu işlemi runtime’da proxy’lerle yapar → **runtime weaving.**

---

### 227) `@Aspect` ve `@Around` nasıl çalışır?

Spring AOP’de bir sınıfı `@Aspect` olarak işaretlersin.  
İçinde metotlara `@Before`, `@After`, `@Around` gibi annotasyonlar eklersin.

```java
@Aspect
@Component
public class LogAspect {
    @Around("execution(* com.example.service.*.*(..))")
    public Object logTime(ProceedingJoinPoint jp) throws Throwable {
        long start = System.nanoTime();
        Object result = jp.proceed(); // orijinal metot çağrısı
        System.out.println(jp.getSignature() + " süresi: " + (System.nanoTime() - start));
        return result;
    }
}
```

Yani `@Around` = Proxy’nin `before` ve `after`’ı birleştirilmiş hali.

---

### 228) `JoinPoint` ve `ProceedingJoinPoint` farkı nedir?

- `JoinPoint`: Sadece metot hakkında bilgi sağlar (metot adı, parametreler vs).
    
- `ProceedingJoinPoint`: `@Around`’da kullanılır ve orijinal metodu çalıştırma (`proceed()`) yetkisine sahiptir.
    

```java
@Around("execution(* com.example..*(..))")
public Object around(ProceedingJoinPoint jp) throws Throwable {
    System.out.println("Before: " + jp.getSignature());
    Object result = jp.proceed();
    System.out.println("After: " + result);
    return result;
}
```

Bu sayede AOP davranışı metot çağrısının etrafına örülür.

---

### 229) AOP ne işe yarar (gerçek dünyada)?

Cross-cutting (katmanlar arası tekrarlanan) işlemleri tek yerde yönetmek için:

- Logging
    
- Exception handling
    
- Security
    
- Caching
    
- Transactions
    
- Metrics & Tracing (Micrometer, OpenTelemetry)
    

Spring Boot’ta `@Transactional`, `@Cacheable`, `@Async` hepsi AOP tabanlıdır.  
Yani “proxy katmanı oluştur, orijinal metodu kontrolle sar.”

---

### 230) AOP runtime’da nasıl işler?

Spring context açılırken:

1. Bean taraması yapılır.
    
2. Eğer bean AOP pointcut’a uyuyorsa, Spring o bean’in **proxy versiyonunu** oluşturur.
    
3. Sen `UserService` çağırdığında aslında `UserService$$EnhancerBySpringCGLIB` sınıfına gitmiş olursun.
    
4. Proxy önce AOP aspect’leri çalıştırır, sonra orijinal metoda geçer.
    

Bu nedenle bazen `this.method()` çağrısı AOP’yi tetiklemez — çünkü proxy bypass olur.  
(İçten çağrı Spring proxy katmanına uğramaz.)

---

### 231) Java Memory Model (JMM) nedir?

Java Memory Model, thread’lerin bellekle nasıl etkileştiğini tanımlar.  
Yani hangi değişkenin kim tarafından ne zaman görülebileceğini belirler.

JMM’in ana amacı: **multi-threaded ortamlarda tutarlılık (consistency)** sağlamak.

Bellek bölgeleri:

- **Heap** → nesneler (object’ler) burada yaşar.
    
- **Stack** → her thread’in kendi değişkenleri.
    
- **Metaspace** → class metadata.
    
- **PC Register & Native Stack** → JVM’in thread içi kayıtları.
    

Spring Boot uygulamaları da bu yapıyı kullanır — her `@Async` çağrısı kendi stack’inde, ama heap paylaşılır.

---

### 232) Heap memory nedir?

Heap, JVM’in **nesneleri** depoladığı alandır.  
Tüm thread’ler bu bölgeyi paylaşır.

Bölümleri:

- **Young Generation** → yeni nesneler (Eden + Survivor alanları).
    
- **Old Generation (Tenured)** → uzun ömürlü nesneler.
    
- **Metaspace** → sınıf yükleme bilgileri.
    

Garbage Collector, heap’i bu bölgeler üzerinden yönetir.  
Spring context, bean’ler, cache objeleri, Hibernate entity’leri burada yaşar.

---

### 233) Stack memory nedir?

Stack, her thread’in **geçici değişkenlerini ve çağrı kayıtlarını** tutar.  
Her `Thread` kendi stack’ine sahiptir.

Örnek:

```java
public int sum(int a, int b) {
    int result = a + b; // stack’te
    return result;
}
```

Stack thread’e özel olduğu için **thread-safe’tir.**  
Ama heap ortak olduğundan orada dikkatli olmak gerekir (özellikle singleton bean’lerde).

---

### 234) Garbage Collector (GC) nedir?

Garbage Collector, **referansı kalmayan nesneleri** temizleyerek belleği geri kazandırır.  
Manuel `free()` yok; JVM bu işi yapar.

GC, “reachability” (erişilebilirlik) analizine göre çalışır:

- Referansı kalmayan nesneler “garbage” olur.
    
- GC bu nesneleri temizler.
    

Java’da popüler GC algoritmaları:

- Serial GC (tek thread, küçük uygulamalar)
    
- Parallel GC (çok çekirdekli)
    
- G1 GC (modern varsayılan)
    
- ZGC & Shenandoah (düşük latency)
    

Spring Boot 3+ uygulamaları genelde G1 GC veya ZGC kullanır.

---

### 235) GC nasıl çalışır? (temel mantık)

GC, “**stop-the-world**” olaylarıyla çalışır:

1. Thread’ler durur.
    
2. GC root’lardan (stack, static, register) erişilebilir nesneleri işaretler.
    
3. Geri kalanları siler (mark-sweep-compact).
    

Yeni nesneler Young Gen’de temizlenir (Minor GC),  
yaşlı nesneler Old Gen’e geçer (Major GC).

Amaç:

> Belleği otomatik yönetmek, performansı korumak, OutOfMemory hatalarını önlemek.

---

### 236) GC tuning nasıl yapılır?

JVM parametreleriyle bellek yönetimini ayarlayabilirsin:

```bash
-Xms512m     # başlangıç heap boyutu
-Xmx1024m    # maksimum heap boyutu
-XX:+UseG1GC # G1 Garbage Collector kullan
-XX:+PrintGCDetails
```

Spring Boot container’da (Docker, Kubernetes) memory limitleri önemlidir.  
G1 GC genelde en dengeli seçimdir.

---

### 237) `OutOfMemoryError` neden olur?

Heap dolmuş ama GC temizleyemiyorsa oluşur.  
Nedenleri:

- Sonsuz nesne üretimi (ör. cache büyümesi)
    
- Memory leak (referans unutulmuyor)
    
- Çok büyük koleksiyonlar
    
- Sonsuz recursive çağrı (Stack Overflow → ayrı hata)
    

Çözüm:

- Heap artır (`-Xmx`)
    
- Nesne ömrünü kısalt
    
- WeakReference veya cache limit kullan
    
- `VisualVM` veya `JFR` (Java Flight Recorder) ile profille.
    

---

### 238) ClassLoader nedir?

ClassLoader, JVM’de **sınıfları belleğe yükleyen mekanizmadır.**

Hiyerarşi:

1. **Bootstrap ClassLoader** → JDK sınıfları (`java.lang.*`)
    
2. **Extension ClassLoader** → eklentiler
    
3. **Application ClassLoader** → senin `classpath`’indeki sınıflar
    

Spring Boot’un kendi `LauncherClassLoader`’ı vardır (fat-jar desteği için).  
Yani sen `java -jar app.jar` dediğinde, Spring kendi ClassLoader’ı ile her dependency’yi yükler.

---

### 239) ClassLoader nasıl çalışır (ve neden önemlidir)?

Bir sınıf ilk kez çağrıldığında:

- ClassLoader bytecode’u bulur ve yükler.
    
- Metaspace’e koyar.
    
- JVM o sınıfın tek kopyasını kullanır.
    

Bu, Spring Boot devtools’un **hot reload** mekanizmasının da temelidir.  
Devtools, kendi “child ClassLoader” oluşturur; sadece değişen sınıfları yeniden yükler.

---

### 240) JVM performansı nasıl izlenir ve optimize edilir?

Gerçek dünyada JVM gözlem araçlarıyla:

- `jconsole`, `jvisualvm`, `jmc` (Java Mission Control)
    
- `jstat`, `jmap`, `jcmd`, `jstack` komutları
    
- `Micrometer + Prometheus + Grafana` entegrasyonu (Spring Boot Actuator üzerinden)
    

Ana odaklar:

- Heap kullanımı (`Used/Committed`)
    
- GC frekansı ve durma süresi
    
- Thread count
    
- Metaspace büyümesi
    

Kritik öneri:

> Backend uygulamalarında “GC pause time” ve “allocation rate” her zaman izlenmeli.

---

### 241. Spring Transactional Isolation Level Nedir? Seviyeleri Nelerdir?

**Transactional Isolation Level**, birden fazla işlemin aynı veritabanı kayıtları üzerinde çalışırken veri bütünlüğünü korumak için kullanılan mekanizmadır.

Spring, JPA veya JDBC üzerinden bu seviyeleri doğrudan destekler:

- **READ_UNCOMMITTED:** Diğer transaction’ların henüz commit edilmemiş verilerini okuyabilir → _Dirty Read riski vardır._
    
- **READ_COMMITTED:** Sadece commit edilmiş veriler okunur → _Non-Repeatable Read mümkündür._
    
- **REPEATABLE_READ:** Aynı transaction içinde aynı sorgular her seferinde aynı sonucu döner → _Phantom Read mümkündür._
    
- **SERIALIZABLE:** En yüksek seviye. Transaction’lar sıralı yürütülür, veri bütünlüğü maksimumdur ama performans düşer.
    

Örnek:

```java
@Transactional(isolation = Isolation.REPEATABLE_READ)
public void processPayment() {
    // tutarlı okuma sağlanır
}
```

---

### 242. @Transactional Nerede Kullanılmamalı? Propagation Nedir?

`@Transactional` anotasyonu genellikle **service katmanında** kullanılmalıdır.  
`@Controller` veya `@Repository` seviyesinde kullanmak, AOP proxy yapısına zarar verebilir.

**Propagation** özelliği, bir transactional metodun çağrıldığı anda mevcut bir transaction olup olmadığını ve yeni bir transaction başlatılıp başlatılmayacağını belirler.

Yaygın türler:

- `REQUIRED`: Varsayılan. Mevcut transaction varsa devam eder, yoksa yenisini açar.
    
- `REQUIRES_NEW`: Her zaman yeni transaction başlatır.
    
- `SUPPORTS`: Transaction varsa katılır, yoksa non-transactional yürütür.
    
- `NOT_SUPPORTED`: Transaction varsa askıya alır.
    

---

### 243. Spring’de Circle Dependency Hatası Nasıl Çözülür?

Circle dependency (dairesel bağımlılık), iki veya daha fazla bean’in birbirine bağımlı olmasıdır.

**Çözümler:**

- `@Lazy`: Bean’lerin yalnızca ihtiyaç duyulduğunda yüklenmesini sağlar.
    
- `@Primary` veya `@Qualifier`: Alternatif bean tanımlayarak Spring’in hangi bean’i kullanacağını belirler.
    
- **Redesign:** Bağımlılıkları soyutlayarak veya interface’lerle yeniden tasarlamak en kalıcı çözümdür.
    

```java
@Service
public class AService {
    private final BService bService;
    public AService(@Lazy BService bService) { this.bService = bService; }
}
```

---

### 244. @Lazy Kullanmadan Circle Dependency Nasıl Çözülür?

Eğer `@Lazy` kullanmak istenmiyorsa, injection noktalarını yeniden yapılandırmak gerekir.  
Örneğin bir taraf constructor injection yerine **setter injection** kullanabilir veya bağımlılık **event tabanlı** hale getirilebilir.

Alternatif olarak `@Primary` veya `@Qualifier` ile spesifik bean seçimi yapılabilir.

---

### 245. Spring Bean Scope Nedir? Türleri Nelerdir?

Spring Bean’lerinin yaşam döngüsü (scope) hangi koşullarda ve kaç defa oluşturulacağını belirler.

- **singleton:** Varsayılan scope, konteyner başına tek örnek.
    
- **prototype:** Her injection isteğinde yeni örnek oluşturulur.
    
- **request:** Her HTTP isteği için yeni örnek (web uygulamalarında).
    
- **session:** Her kullanıcı oturumu için tek örnek.
    

```java
@Scope("prototype")
@Component
public class TaskProcessor {}
```

---

### 246. ApplicationContext Nedir?

Spring’in temel yapı taşıdır. Bean’lerin oluşturulması, bağımlılıkların çözülmesi, event yönetimi ve uluslararasılaştırma gibi görevleri üstlenir.

`ApplicationContext`, `BeanFactory`’nin gelişmiş bir versiyonudur.  
Ek olarak:

- Event Publishing
    
- Annotation Scanning
    
- MessageSource (i18n desteği) sağlar.
    

```java
ApplicationContext context = new AnnotationConfigApplicationContext(AppConfig.class);
MyService service = context.getBean(MyService.class);
```

---

### 247. Bir Spring Projesinde Birden Fazla Config Dosyası Kullanılır mı?

Evet. Spring, çoklu yapılandırma dosyalarını destekler.  
Farklı modülleri veya ortamları ayırmak için birden fazla `@Configuration` sınıfı oluşturulabilir.

```java
@Configuration
@Import({DatabaseConfig.class, SecurityConfig.class})
public class AppConfig {}
```

Bu, projeyi **modüler** ve **okunabilir** hale getirir.

---

### 248. Spring IOC (Inversion of Control) Nedir? Türleri Nelerdir?

IOC, nesnelerin yaşam döngüsünün uygulama tarafından değil, Spring Container tarafından yönetilmesi anlamına gelir.

**İki tür bağımlılık enjeksiyonu vardır:**

1. **Constructor Injection:** Bağımlılık, constructor üzerinden alınır.
    
2. **Setter Injection:** Bağımlılık, setter metoduyla atanır.
    

IOC, test edilebilirliği artırır ve loosely coupled (gevşek bağlı) mimari sağlar.

---

### 249. @Service, @Component, @Repository Arasındaki Fark Nedir?

Spring bileşenlerinin katmanlara göre ayrılmasını sağlar:

- `@Component`: Genel amaçlı bileşen.
    
- `@Service`: İş (business) katmanını temsil eder.
    
- `@Repository`: Veri erişim katmanını temsil eder, otomatik exception çevirimi (PersistenceExceptionTranslation) içerir.
    

Tüm bu anotasyonlar `@Component`’in specialization’ıdır (alt türüdür).

---

### 250. @ConditionalOnProperty Nedir?

Bir property değerine göre bean’in oluşturulup oluşturulmayacağını belirler.

```java
@ConditionalOnProperty(name = "feature.enabled", havingValue = "true")
@Service
public class FeatureService {}
```

Bu yaklaşım, **feature toggle** veya **ortam bazlı konfigürasyonlar** için idealdir.

---

### 251. SpEL (Spring Expression Language) Nedir?

Spring Expression Language, Spring bean’leri içinde dinamik değerler hesaplamak için kullanılan güçlü bir ifade dilidir.

```java
@Value("#{systemProperties['user.name']}")
private String currentUser;
```

Ayrıca SpEL, bean property erişimi, metot çağrıları, koleksiyon işlemleri ve koşullu ifadeleri destekler.

---

### 252. @JsonIgnore, @JsonInclude, @JsonView Nedir?

JSON serileştirme/deserileştirme işlemlerini kontrol ederler.

- `@JsonIgnore`: Alanın JSON’a dahil edilmesini engeller.
    
- `@JsonInclude`: Belirli koşullarda alanları dahil eder (ör. `Include.NON_NULL`).
    
- `@JsonView`: Farklı görünüm seviyeleri tanımlar, API çıktısını özelleştirir.
    

Örnek:

```java
@JsonInclude(JsonInclude.Include.NON_NULL)
public class User {
    private String name;
    @JsonIgnore private String password;
}
```

---

### 253. Spring Cache Anotasyonları Nelerdir?

Spring, caching için entegre anotasyon desteği sunar:

- `@Cacheable`: Metot sonucu cache’e alınır.
    
- `@CachePut`: Cache güncellenir.
    
- `@CacheEvict`: Cache temizlenir.
    
- `@EnableCaching`: Caching desteğini aktif hale getirir.
    

Örnek:

```java
@Cacheable("users")
public User getUserById(Long id) { ... }
```

---

### 254. Spring’de İç İçe Çağrımlarda Transaction Açılmasını İstemediğimiz Metoda Ne Yapılır?

Propagation seviyesini değiştirerek kontrol edilir:

```java
@Transactional(propagation = Propagation.NOT_SUPPORTED)
public void nonTransactionalMethod() { ... }
```

Bu durumda metot çağrıldığında mevcut transaction askıya alınır ve işlem transactional yürütülmez.

---

### 255. @Service Anotasyonunu Kullanmazsak Ne Olur?

Spring, bileşeni otomatik olarak bean olarak tanımaz.  
Bu durumda o sınıfın bir örneği oluşturulmaz ve `NoSuchBeanDefinitionException` fırlatılır.

Alternatif olarak manuel bean tanımı yapılabilir:

```java
@Bean
public MyService myService() { return new MyService(); }
```

---

### 256. Spring Circle Dependency Problemi Redesign ile Nasıl Çözülür?

Bağımlılık yönünü tersine çevirmek veya event tabanlı bir mimari kurmak gerekir.

Örneğin:

- `ApplicationEventPublisher` kullanarak bağımlı sınıflar arasındaki doğrudan bağlantıyı koparabilirsiniz.
    
- Interface tabakası eklenerek bağımlılık yönü tek yöne çevrilebilir.
    

---

### 257. Spring Bean Yaşam Döngüsü Nasıldır?

1. Bean tanımı okunur.
    
2. Constructor veya factory method çağrılır.
    
3. Dependency injection yapılır.
    
4. `@PostConstruct` metodları çalışır.
    
5. Bean kullanılabilir hale gelir.
    
6. Context kapandığında `@PreDestroy` metodları çağrılır.
    

---

### 258. Spring’te ApplicationContext’in Olay (Event) Mekanizması Nedir?

Spring, kendi event yayınlama sistemiyle event-driven yapıları destekler.

```java
@Component
public class MyListener implements ApplicationListener<MyEvent> {
    public void onApplicationEvent(MyEvent event) { ... }
}
```

```java
applicationContext.publishEvent(new MyEvent(this, "data"));
```

Bu sistem, modüller arası bağımlılığı azaltır.

---

### 259) Bir interface’de 5 metot var; ben sadece 2’sini kullanacağım, ne yaparım?

**Ana stratejiler (pratikten kanıtlı):**

- **Adapter/Abstract Base (önerilen):** Interface için bir **abstract adapter** yaz, gereksiz metotları **no-op** bırak; gerçek sınıf adapter’ı extend edip yalnızca gereken 2 metodu override eder.
    
- **UnsupportedOperationException:** Kullanmayacaklarına `throw new UnsupportedOperationException()` fırlat; niyet netleşir.
    
- **`default` metotlar:** Interface **seninse**, gereksizlere `default` gövde ver; binary uyumluluğu korursun.
    
- **Kompozisyon/delege:** Geniş interface’in yanında **dar bir port** (2 metotluk küçük arayüz) tanımla; implementasyon bu dar porta programlansın.
    

**Mini örnek (adapter):**

```java
interface BigApi {
  void a(); void b(); void c(); void d(); void e();
}

abstract class BigApiAdapter implements BigApi {
  public void a() {}
  public void b() {}
  public void c() {}
  public void d() {}
  public void e() {}
}

class OnlyAB extends BigApiAdapter {
  @Override public void a() { /* logic */ }
  @Override public void b() { /* logic */ }
}
```

**Dikkat:** 3rd-party interface’e `default` ekleyemezsin. Geniş interface kokusunu (interface segregation) fark ettiysen uzun vadede **dar arayüzlere böl**.

---

### 260) Enum’a `abstract` metot yazarsam ne olur?

- Enum içinde `abstract` metot tanımlanabilir; **her constant** bunu **override etmek zorunda**.
    
- Farklı constant’lar farklı strateji gibi çalışabilir (Strategy benzeri).
    

**Örnek:**

```java
enum Op {
  ADD { int apply(int a,int b){ return a+b; } },
  MUL { int apply(int a,int b){ return a*b; } };
  abstract int apply(int a, int b);
}
```

**Not:** Enum başka sınıfı **extend edemez** (zaten `java.lang.Enum`’u extend eder); interface implement edebilir.

---

### 261) `javac` nedir?

- **Derleyici**: `.java` → `.class` bytecode.
    
- **Sürüm hedefleme:** `--release 21` (tek bayrakla rt kütüphane + dil seviyesi uyumu).
    
- **Classpath/Modules:**
    
    - Classpath: `-cp libs/*`
        
    - Modüller: `--module-path mlib --module your.module`
        
- **Annotation processing:** `-processor`, `-proc:only`
    
- **Uyarılar/Debug:** `-Xlint:all -Werror -g`
    
- **Parametre isimleri (reflection için):** `-parameters`
    

**Örnek:**

```bash
javac --release 21 -Xlint:all -parameters -d out $(find src -name "*.java")
```

---

### 262) Stream `filter` hangi parametreyi alır?

- **`Predicate<? super T>`**. `true` dönenler akışta kalır.
    
- **Saf (pure) tut**: Yan etki yazma, dış state’e bağımlı olma.
    

**Örnek:**

```java
List<String> names = List.of("Ali","Ayşe","Veli");
var shortOnes = names.stream()
                     .filter(s -> s.length() <= 3) // Predicate<String>
                     .toList();
```

---

### 263) Kafka partition assignment stratejileri (consumer group)

**Konfig:** `partition.assignment.strategy`  
Seçenekler ve davranış:

- **RangeAssignor:** Aralık bazlı dağıtır; partition sayıları/topic dağılımı eşit değilse dengesizlik olabilir.
    
- **RoundRobinAssignor:** Teker teker sırayla dağıtır; genelde daha dengeli.
    
- **StickyAssignor / CooperativeStickyAssignor (güncel tercih):** Rebalance’da **minimum hareket** + **inkremental** el değiştirme → **daha az duraklama**.
    

**Pratik öneri:** Prod’da **`CooperativeStickyAssignor`** çoğu senaryoda en az kesinti.

---

### 264) Uzak (remote) Kafka consumer performansı nasıl iyileştirilir?

**Temel etkenler:** RTT (gecikme), bant genişliği, mesaj boyutu, partition dağılımı.

**Consumer tuning:**

- Batch/istek sayısı: `fetch.min.bytes`, `fetch.max.wait.ms`, `max.partition.fetch.bytes`
    
- Soket buffer’ları: `receive.buffer.bytes` (OS limite dikkat)
    
- Poll davranışı: `max.poll.records`, `max.poll.interval.ms` (işleme sürene göre ayarla)
    
- Parallelizm: **partition sayısı ≥ consumer paralelliği**
    

**Üretici tarafı da önemlidir:**

- `compression.type` (lz4/zstd), `linger.ms`, `batch.size` ile **daha büyük batch** → **daha az round-trip**
    
- **Cross-region** kaçınılmazsa: **VPC peering**, MTU/packetization, TLS maliyeti (CPU) planlaması.
    

**Gözlemle:** Consumer lag, bytes in/out, fetch rate; **throttle** ve **rebalance** olaylarını izle.

---

### 265) Cloud development (sahada gerçekten olan)

- **12-Factor** ilkeleri: config dışarıda, stateless process, disposability.
    
- **IaC & GitOps:** Terraform/Pulumi; ArgoCD/Flux ile deklaratif dağıtım.
    
- **CI/CD:** Mavi-yeşil, canary; artifact imzası (SBOM, SLSA).
    
- **Managed servisler:** DB, queue, cache’i yönetilenden al; az operasyonel yük.
    
- **Observability:** Tracing (OpenTelemetry), metrics (Micrometer/Prometheus), logs.
    
- **Day-2 ops:** Autoscaling, chaos drills, bütçe alarmları (cost guardrails), SLO/SLI.
    

**Kısayol:** “Önce platform guardrail’lerini kur, sonra uygulama koş.” Güvenlik, gözlemlenebilirlik ve maliyet duvarları **en başta**.

---

### 266) Redis cluster mode vs standalone

- **Standalone:** Basit, tek düğüm; **tek hata noktası**, yatay ölçek yok. Sentinel ile **yalnızca failover** (shard yok).
    
- **Cluster:** 16.384 **hash slot**; sharding + replika + otomatik failover. **Multi-key** işlemler **aynı slot** gerektirir; `EVAL`/transaction sınırlarına dikkat.
    

**Ne zaman hangisi?**

- **Kritik veri, yüksek trafik** → Cluster.
    
- **Basit cache, düşük hacim** → Standalone + Sentinel yeterli olabilir.
    

---

### 267) Hibernate N+1 problemi

**Belirti:** Koleksiyon/ilişkiyi her satır için ayrı sorgu çekmesi.

**Tespit:**

- SQL log’u aç (`hibernate.show_sql`/`org.hibernate.SQL=DEBUG`).
    
- Prod’da APM/trace ile sorgu sayısı ve sürelerini izle.
    

**Çözümler (başarı sırası pratikte):**

1. **`JOIN FETCH` / `@EntityGraph`**: Hedefli eager.
    
2. **Batch fetch**: `@BatchSize(size=...)` veya `hibernate.default_batch_fetch_size`.
    
3. **`SUBSELECT`**: Koleksiyonlar için tek ek sorgu ile toplama.
    
4. **DTO projection**: İhtiyaç kadar alan çek.
    

**Karşı-örnek:** Aynı entity’de **iki “bag” koleksiyonu** `JOIN FETCH` ile beraber → kartesyen patlama. Parçala.

---

### 268) Immutable class nasıl doğru tasarlanır?

**Kurallar:**

- Alanlar: `private final`
    
- Setter **yok**
    
- **Defansif kopya**: `Date`, `List`, `Map` gibi mutable alanlar için kopya al/ver
    
- Sınıf mümkünse `final`
    
- Eşitlik: `equals/hashCode` yalnızca alanlara
    

**Örnek (temiz):**

```java
public final class User {
  private final String id;
  private final List<String> roles;

  public User(String id, List<String> roles) {
    this.id = id;
    this.roles = List.copyOf(roles); // defensive copy
  }
  public String id() { return id; }
  public List<String> roles() { return roles; } // already unmodifiable
}
```

**Alternatifler:**

- **`record`** (Java 16+): Doğası gereği immutability.
    
- **Lombok `@Value`**: final alanlar + getter + equals/hashCode + toString.
    

**Dikkat:** Immutable nesneler concurrency’de **bedava thread-safe**; ama büyük koleksiyonlarda kopya maliyetini ölç.

---

### 269) DDD (Domain-Driven Design) nedir?

- **Amaç:** Karmaşık iş kurallarını kodla **aynı dilde** ifade etmek ve değişimi **domain sınırları**yla yönetmek.
    
- **Temel taşlar:**
    
    - **Ubiquitous Language:** İş ekipleriyle aynı terimleri kodda kullan.
        
    - **Bounded Context:** Kavramların anlamı **bağlama özgüdür**; tek “User” modeli yerine her bağlamda ayrı “User”.
        
    - **Aggregate & Root:** Tutarlılık sınırı; dış dünya **sadece Root** üzerinden değişiklik yapar.
        
    - **Value Object:** Kimliksiz, eşitlik **değer** üzerinden; immutable tasarla.
        
    - **Domain Event:** “Ne oldu?”yu açıkla; bağlamlar arası entegrasyon için altın değer.
        
- **Uygulama ipuçları:**
    
    - **Katmanlı yapı:** API / Application / Domain / Infra.
        
    - Servisler “orkestrasyon”, **domain model** iş kuralıdır.
        
    - Anti-corruption layer ile eski sistemleri **izole** et.
        
- **Kırmızı bayraklar:** Anemik domain (sadece getter/setter), devasa “God Service”, bağlamlar arası sızıntı.
    

---

### 270) Kafka’da consumer group nedir, ne işe yarar?

- **Paralel tüketim:** Bir topic’in **her partition’ı grup içinde tek consumer** tarafından işlenir → **doğrusal ölçek** = partition sayısı.
    
- **Dayanıklılık:** Offset’ler **grup kimliği** ile tutulur; consumer yeniden başladı mı kaldığı yerden devam eder.
    
- **Tuning:**
    
    - **Rebalance süreleri:** `max.poll.interval.ms`, `session.timeout.ms`, `heartbeat.interval.ms`.
        
    - **İşleme süresi uzun** akışlarda `max.poll.interval.ms` artır; aksi halde consumer “ölü” sanılır.
        
    - **Idempotent işleme** ve **retry-DLQ** stratejisini gruba göre kurgula.
        

---

### 271) JPA Projection nedir?

- **Neden:** Entity’nin tamamını çekmek **şişkinlik** ve **N+1** tetikler. Sadece ihtiyacın olan alanları al.
    
- **Türler:**
    
    - **Interface projection (closed):**
        
        ```java
        interface UserView { String getId(); String getEmail(); }
        List<UserView> findByActiveTrue();
        ```
        
    - **DTO projection (constructor):**
        
        ```java
        record UserDto(String id, String email) {}
        @Query("select new com.acme.UserDto(u.id, u.email) from User u where u.active = true")
        ```
        
    - **Native/ResultSet mapping:** Şema-özeline in, ama taşınabilirlik azalır.
        
- **Not:** Projection + **join fetch** karışımlarında kartesyen patlamaya dikkat.
    

---

### 272) Spring’in default server’ı nedir, nasıl değişir?

- **Varsayılan:** Embedded **Tomcat** (blocking I/O).
    
- **Alternatif:** **Jetty** veya **Undertow** (non-blocking).
    
- **Geçiş:** Tomcat starter’ı çıkar, Jetty/Undertow starter’ı ekle.
    
    ```xml
    <!-- pom.xml -->
    <dependency>
      <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-web</artifactId>
      <exclusions>
        <exclusion>
          <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-tomcat</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
    <dependency>
      <groupId>org.springframework.boot</groupId><artifactId>spring-boot-starter-jetty</artifactId>
    </dependency>
    ```
    
- **Seçim kriteri:** **Thread modeli**, **yük profili**, **uyumluluk**.
    

---

### 273) Stream vs Collection

- **Collection:** Veri **deposu**; çok kez iterate edilir.
    
- **Stream:** Veri **boru hattı**; lazy, **tek sefer** tüketim; ara işlemler (map/filter), terminal işlem (collect/reduce).
    
- **Yan etkiler:** Stream zincirini **saf** tut; paralel akışta paylaşılan mutable state’ten kaçın.
    
- **Kısa örnek:**
    
    ```java
    var sum = orders.stream()
                    .filter(o -> o.isPaid())
                    .mapToLong(Order::amountCents)
                    .sum();
    ```
    

---

### 274) `Supplier` ne işe yarar?

- **Tanım:** Girdi almadan değer üretir → `T get()`.
    
- **Kullanımlar:**
    
    - Lazy yaratım: `memoizedSupplier.get()` ilk çağrıda üretir, sonra aynı değeri döner.
        
    - Retry/backoff: Başarısız işlemi tedarikçi fonksiyonla sar.
        
    - Default değer: Map/getOrDefault kalıpları.
        
- **Mini örnek (memoize):**
    
    ```java
    static <T> Supplier<T> memoize(Supplier<T> s) {
      final AtomicReference<T> ref = new AtomicReference<>();
      final AtomicBoolean init = new AtomicBoolean(false);
      return () -> {
        if (init.compareAndSet(false, true)) ref.set(s.get());
        return ref.get();
      };
    }
    ```
    

---

### 275) `volatile` ne sağlar, ne sağlamaz?

- **Sağlar:** Görünürlük ve **happens-before** sıralaması. Her okuma/yazma **main memory** üzerinden; CPU cache tutarsızlıkları olmaz.
    
- **Sağlamaz:** **Atomiklik** veya bileşik işlemler (örn. `x++`) için güvenlik.
    
- **Doğru kullanım:**
    
    - **İşaret bayrağı** (stopFlag).
        
    - **Tek üretici-tek tüketici** gibi hafif senaryolarda state görünürlüğü.
        
- **Sayaç/istatistik için:** `AtomicLong`, yoğun yazım altında `LongAdder` daha iyi.
    
- **Örnek:**
    
    ```java
    class Worker {
      private volatile boolean running = true;
      void stop() { running = false; }
      void loop() { while (running) { /* work */ } }
    }
    ```
    

---

### 276) `@Data`, `@Getter`, `@Setter` (Lombok)

**Kısa kural:**

- **DTO/response** objeleri **immutability** istiyorsa: `record` (Java 16+) **veya** `@Getter` + `final` alanlar + `@Builder`.
    
- **Entity** (JPA) için **`@Data` önermem**: `equals/hashCode` ilişkilerde döngü ve performans sorununa davetiye çıkarır; `toString` da aynı.
    
- Basit POJO’da sadece ihtiyaç kadar aç: **`@Getter`**; çok nadir gerekenlere **`@Setter`**.
    

**Yaygın hatalar ve çözümler:**

- `@Data` + JPA entity → **Hayır**. Onun yerine:
    
    ```java
    @Getter @Setter // alan bazlı kontrollü
    @EqualsAndHashCode(onlyExplicitlyIncluded = true)
    @ToString(of = {"id","email"})
    class User { @EqualsAndHashCode.Include Long id; String email; ... }
    ```
    
- Builder lazım ama koleksiyonlar var → `@Builder` + `@Singular`.
    
- Serileştirme (Jackson) yapıyorsan **no-args ctor** ihtiyacı → `@NoArgsConstructor(force = true)` + `@AllArgsConstructor`.
    

---

### 277) `@Stereotype` nedir? Spring vs CDI

- **Spring’de** `@Stereotype` diye **özel bir anotasyon yok**; `@Component`, `@Service`, `@Repository`, `@Controller` gibi **stereotype anotasyonlar** var.
    
- **CDI (Jakarta)** dünyasında “stereotype” bir meta-anotasyon kavramıdır.
    
- Spring’de kendi bileşik anotasyonunu oluşturabilirsin:
    
    ```java
    @Target(TYPE)
    @Retention(RUNTIME)
    @Component
    public @interface UseCase { }
    ```
    
    Böylece `@UseCase` ile iş kuralı sınıflarını taramaya dahil edersin; anlam da kazanır.
    

---

### 278) Sistemler arası iletişim

**REST (HTTP/JSON)**

- Artılar: Yaygın ekosistem, gateway/observability kolay.
    
- Eksiler: Sözleşme zayıf (OpenAPI şart), over/under-fetch riski.
    
- Kullan: Genel amaçlı, internet ölçeğinde API.
    

**gRPC (HTTP/2 + Protobuf)**

- Artılar: Sıkı sözleşme, düşük bant genişliği, streaming.
    
- Eksiler: Tarayıcı native desteği sınırlı (genelde proxy).
    
- Kullan: **Mikroservis-içi** düşük gecikme, yüksek throughput.
    

**GraphQL**

- Artılar: Tek endpoint, istemci istediğini çeker.
    
- Eksiler: N+1, caching & auth karmaşıklığı.
    
- Kullan: Çok farklı istemci/ekranlar, esnek veri ihtiyaçları.
    

**SOAP**

- Artılar: Resmi sözleşme, kurumsal entegrasyon, WS-*.
    
- Eksiler: Ağır; modern dünyada sınırlı.
    
- Kullan: Mevcut kurumsal sistemlerle zorunlu entegrasyon.
    

**MQ (Kafka/RabbitMQ)**

- Artılar: Gevşek bağlılık, backpressure, retry/DLQ.
    
- Eksiler: Operasyonel karmaşıklık, en sonunda **consistency** konusu.
    
- Kullan: Asenkron süreçler, entegrasyon, event-driven.
    

---

### 279) İki faktörlü erişim (2FA)

**Faktör tipleri:**

- **Bilgi:** Şifre.
    
- **Sahiplik:** TOTP (Google Authenticator), SMS (zayıf), **FIDO2/U2F (güçlü)**.
    
- **Biyometri:** Parmak izi/yüz (genelde cihaz bağlamında).
    

**Öneriler:**

- **TOTP** (RFC 6238) + **backup codes** zorunlu kıl.
    
- Mümkünse **WebAuthn/FIDO2** ekle (phishing dirençli).
    
- Brute-force’a karşı **rate limit** ve **device binding** uygula.
    
- **Saat kayması** (drift) için ±30–60 sn tolerans; başarısız girişleri logla ve uyarı üret.
    

---

### 280) `List.of` nedir? `immutable` vs `unmodifiable`

- `List.of(...)` **gerçekten immutable** bir liste döndürür: `add/remove/set` → **`UnsupportedOperationException`**; **`null` kabul etmez**.
    
- `List.copyOf(collection)` koleksiyonun **değiştirilemez bir kopyasını** döndürür (kaynak zaten unmodifiable ise aynısını).
    
- `Collections.unmodifiableList(new ArrayList<>(...))` **sargı**dır; alttaki liste değişirse dışarı yansır (yanlış anlaşılır).
    
- `Arrays.asList(...)` **sabit boyutlu** (structural mod yok), ama `set` yapılabilir.
    

**Kısa kural:** Paylaşılacak sabit veri için `List.of`; var olanı kilitlemek için `List.copyOf`.

---

### 281) JS arrow function & ECMAScript sürümü

**Arrow function:**

- Kısa sözdizimi + **lexical `this`**; `function`’daki `this` tuzaklarını azaltır.
    
- `arguments`, `new.target` gibi bağlamları **yoktur**; constructor olarak **kullanılamaz**.
    

```js
const double = x => x * 2;
const obj = {
  val: 41,
  incLater() { setTimeout(() => { this.val++; }, 0); } // lexical this
};
```

**ECMAScript sürümü:**

- Her yıl **ES20xx** olarak yayınlanır. “En son” sürüm **yıla bağlıdır**; pratikte önemli olan hedef ortam (tarayıcı/Node) desteği. Yeni dil özelliği kullanacaksan **Babel/TS** transpile stratejini belirle ve **core-js** polyfill planı yap.
    

---

### 282) Stop-the-World (STW) — ne zaman, nasıl kısaltılır?

**Ne zaman:** GC’in belirli fazlarında tüm uygulama thread’leri durur. G1, ZGC, Shenandoah **STW süresini kısaltır** ama sıfırlamaz.

**Etkileyenler:**

- **Heap boyutu, canlı veri (live set), allocation rate**
    
- **Safepoint** yoğunluğu, dev objeler (humongous in G1)
    

**Ayarlamalar:**

- G1: `-XX:+UseG1GC -XX:MaxGCPauseMillis=200` (hedef; garanti değildir)
    
- Büyük objeleri azalt; **objeyi yeniden kullan** (escape analysis’ı bozma).
    
- **TLAB** etkin (varsayılan); kıymetli ise `-XX:+PrintTLAB` ile izle.
    
- **Profil:** JFR (Java Flight Recorder) ile **GC Pause**, **Allocation Pressure** grafiğine bak.
    

---

### 283) `flush` sadece commit’te olsun; `select` tetiklemesin

**Çözüm:**

- Global: `spring.jpa.properties.hibernate.flushMode=COMMIT`
    
- Ya da EntityManager/Query bazlı:
    
    ```java
    entityManager.setFlushMode(FlushModeType.COMMIT);
    query.setFlushMode(FlushModeType.COMMIT);
    ```
    

**Bilmen gerekenler:**

- Hibernate **auto-flush** stratejisi bazı `SELECT`lerde tutarlılık için flush ister; `COMMIT`’e alınca bunu ertelersin.
    
- Native SQL ile çalışırken otomatik flush beklentin farklı olabilir; transaction sınırlarını net tut.
    
- **Toplu okuma (read-only)** sorgular için: `@Transactional(readOnly = true)` ve `hibernate.default_batch_fetch_size` gibi ayarlara odaklan.
    

---

### 284) JMX

**Ne işe yarar:** JVM ve uygulama MBean’leri üzerinden **metrik/operasyon** sunar (heap, thread, GC; app-özel sayaçlar).

**Kullanım yolları:**

- Araçlar: `jconsole`, `jvisualvm`, **JMC**.
    
- Spring Boot:
    
```properties
    management.endpoints.jmx.exposure.include=*
    management.endpoint.jmx.enabled=true
    spring.jmx.enabled=true
    
    @ManagedResource
    class CacheStats {
      @ManagedAttribute public long getHitRate() { ... }
      @ManagedOperation public void reset() { ... }
    }
```
    
- Prometheus için **JMX Exporter** ile metrikleri scrape et.
    

**Güvenlik:** Uzak JMX açacaksan TLS/sasl ve firewall şart; aksi halde risk.

---

### 285) ACID vs BASE

**ACID (OLTP klasik)**

- **Atomisite, Tutarlılık, İzolasyon, Kalıcılık**
    
- Bankacılık, stok, rezervasyon gibi **anomaliye tahammül yok** senaryolar.
    

**BASE (dağıtık/NoSQL)**

- **Basically Available, Soft state, Eventual consistency**
    
- Küresel okuma hacmi yüksek, yazı-yoğun, **partisyon toleransı** isteyen sistemler.
    

**Karar:**

- **CAP üçgeni** (Consistency–Availability–Partition Tolerance) bağlamında düşün.
    
- BASE seçtiysen: **quorum** (R+W>N), **read-repair**, **conflict resolution** (CRDT, LWW, app-level merge) stratejilerini netleştir.
    
- Karma mimari: **CQRS + Event Sourcing** ile yazma ACID, okuma BASE yapılabilir; ama **operasyonel karmaşıklığı** göze al.
    

---

### 286) Idempotency

**Tanım:** Aynı isteği **tekrar tekrar** göndersen de **son durumun değişmediği** işlem.  
**HTTP bağlamı:** `PUT`, `DELETE` varsayılan olarak idempotent; `POST` **değil** (ama key ile idempotent yapılabilir).

**Uygulama desenleri:**

- **Idempotency-Key (önerilen):** İstek header’ı `Idempotency-Key: <guid>`; sunucu bu anahtarı **işlem sonucu** ile birlikte **idempotency store**’da (Redis/DB) saklar, aynı anahtar gelirse **önceki yanıtı** döner.
    
- **Doğal benzersizlik:** Örn. `orderId` unique; aynı `orderId` ile tekrar deneme → no-op.
    
- **Outbox + de-dup:** Event yayınında `messageId` benzersiz; consumer tarafında **işlendi kayıtları** tut.
    

**Köşe taşları:**

- **At-least-once** teslimatta **yan etkileri** (DB yazımı, email, para transferi) dedup et.
    
- **Zaman penceresi** tanımla (key TTL) ve **sadece güvenli alanlarda** cache’le.
    
- Yanıtı da sakladığın için **tam deterministik** dönersin.
    

**Basit örnek (pseudo):**

```java
String key = request.getHeader("Idempotency-Key");
return store.computeIfAbsent(key, () -> executeOnceAndPersistResponse(request));
```

---

### 287) JPA vs Hibernate

- **JPA:** Sadece **spesifikasyon** (arayüzler, anotasyonlar). Uygulama **seç**mek zorundasın.
    
- **Hibernate:** JPA’nın **en yaygın implementasyonu** + ekstra yetenekler (StatelessSession, second-level cache ayrıntıları, natural id, vs).
    

**Ne kullanmalı?**

- **API olarak JPA**, **motor olarak Hibernate** yaklaşımı en esnek olanı. Kod JPA’ya programlanır, gerekirse motoru değiştirebilirsin.
    

**Alternatifler:**

- **EclipseLink**, **OpenJPA** (ORM).
    
- **jOOQ**: ORM değil; **tip-güvenli SQL DSL**. Kompleks SQL ağırlıklı projelerde muazzam.
    

**Pratik notlar:**

- JPA/Hibernate ile **N+1** ve **şişkin entity** riskini projection/DTO ile azalt.
    
- Native SQL gerektiğinde korkma; JPA `@SqlResultSetMapping` ya da doğrudan JDBC/jOOQ.
    

---

### 288) Apache Solr

**Ne:** Lucene üzerinde kurulu, **full-text arama** ve **facet** motoru.  
**Özellikler:** Schema yönetimi, sharding/replication, highlighting, analyzers, query parsers (edismax), collection yönetimi.

**Kullanım alanları:**

- Site içi arama, katalog/ürün araması, log & doküman arama, faceted navigation.
    
- Zengin **facet** ve **keyword scoring** senaryolarında güçlü.
    

**Solr vs ES kısa fark:**

- Solr **çok özelleştirilebilir** query parser ve schema yönetiminde esnek.
    
- ES **JSON-first** API ve ekosistem araçlarında (beats, kibana) daha pratik.
    
- Karar: Ekip yetkinliği + operasyonel kısıtlar.
    

**Tuning ipuçları:** Doğru analyzer/tokenizer, field-type, **docValues**; filtreleri **cache**; sıcak shard replikalarını izole et.

---

### 289) Java Agent

**Ne:** JVM başlarken `-javaagent:agent.jar` ile yüklenip sınıfların **bytecode**’una enstrümantasyon/transformasyon uygulayan parça.

**Kullanımlar:**

- **APM/Profil:** Metot süreleri, SQL izleme, dağıtık iz.
    
- **Güvenlik:** Policy enforcement, kanca takma.
    
- **Log/Trace zenginleştirme:** MDC/Span id otomasyonu.
    

**Temel API:**

- `premain(String args, Instrumentation inst)` → startup’ta
    
- `agentmain` → runtime attach (tools.jar / Attach API)
    
- `ClassFileTransformer` ile bytecode rewrite.
    

**Dikkat:**

- Sürüm/bytecode uyumu, **performans** ve **classloading** etkileri.
    
- Gölge bağımlılık (shading) ve minimal yüzey alanı.
    

---

### 290) Double-brace initialization

**Örnek (kötü):**

```java
Set<String> s = new HashSet<>() {{ add("A"); add("B"); }};
```

**Sorunlar:**

- **Anonim inner class** yaratır → fazladan sınıf/metaveri.
    
- **Serileştirme** ve **memory leak** riskleri.
    
- Eşitlik/`equals` davranışında sürprizler.
    

**Doğru alternatifler:**

```java
Set<String> s = Set.of("A", "B");         // immutable
List<String> l = new ArrayList<>(List.of("A","B")); // mutable kopya
Map<String,Integer> m = Map.of("a",1,"b",2);
```

---

### 291) Spring’de çoklu veritabanı (multi-DB)

**Amaç:** Farklı DB’ler (örn. `primary` = OLTP, `analytics` = rapor) için **ayrı EM/Tx**.

**Adımlar:**

1. **İki `DataSource` bean** (birine `@Primary`).
    
2. Her DS için **`LocalContainerEntityManagerFactoryBean`**.
    
3. Her biri için **`PlatformTransactionManager`**.
    
4. Repository paketlerini **adresle**:
    

```java
@EnableJpaRepositories(
  basePackages = "com.acme.repo.primary",
  entityManagerFactoryRef = "emfPrimary",
  transactionManagerRef   = "txPrimary"
)
```

5. Kullanımda `@Transactional("txPrimary")` veya `@Qualifier` ile seçim.
    

**Dikkat:**

- **Cross-DB transaction** gerekiyorsa 2PC/JTA karmaşıklığı (kaçın, mümkünse **işlemsel sınırları** net böl).
    
- Healthcheck, migration, seeding süreçlerini **ayrı** kurgula.
    

---

### 292) SOLID — S: Single Responsibility Principle (SRP)

**Öz:** Bir sınıfın **tek bir değişim nedeni** olsun.  
**Belirti:** “Bu sınıf şunları da yapıyor…” demeye başladıysan böl.

**Nasıl uygularım?**

- **Modülerleştir:** Command/Handler, Strategy, Policy objeleri.
    
- **Boundary çiz:** API (giriş) / Application (orkestrasyon) / Domain (iş kuralı) / Infra (yan etkiler).
    

**Kazanç:** Test kolaylığı, değişim izolasyonu, düşük coupling.

---

### 293) CQRS

**Kavramsal:** **Command** (yazma) modeli ile **Query** (okuma) modelini **ayrı** tut.  
**Artılar:** Performans (okuma farklı ölçeklenir), model netliği, güvenli sakınma (okuma **denormalize**).  
**Eksiler:** **Operasyonel karmaşıklık**, veri senkronizasyonu (event propagation).

**Ne zaman?:**

- Okuma → çok yüksek RPS, yazma → kompleks tutarlılık.
    
- Farklı SLİ/SLÖ hedefleri.
    

**Uygulama:**

- **Command side** ACID (RDBMS), **Query side** BASE (cache/NoSQL).
    
- **Event Sourcing** ile birleşirse geçmiş/denetim izi hediyesi; ama karmaşıklık büyür.
    

---

### 294) Dockerfile

**İlkeler:**

- **Multi-stage build**: Dev bağımlılıklarını final imaja taşıma.
    
- **Küçük base image**: `eclipse-temurin:21-jre-alpine` gibi.
    
- **Layer cache**: Sık değişen dosyaları **sona** koy; `COPY` sırasını önemse.
    
- **Kök olmayan kullanıcı**: `USER 1000:1000`.
    
- **Sağlık kontrolü**: `HEALTHCHECK`.
    
- **JVM konteyner farkındalığı**: Java 10+ otomatik; yine de `-XX:MaxRAMPercentage` gözden geçir.
    

**Örnek:**

```dockerfile
# build
FROM eclipse-temurin:21-jdk AS build
WORKDIR /src
COPY . .
RUN ./mvnw -q -DskipTests package

# run
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=build /src/target/app.jar /app/app.jar
EXPOSE 8080
USER 1000:1000
HEALTHCHECK --interval=30s --timeout=3s CMD wget -qO- http://localhost:8080/actuator/health || exit 1
ENTRYPOINT ["java","-jar","/app/app.jar"]
```

**Konteyner JVM hatırlatmaları:**

- K8s `resources.limits.memory` → **`OutOfMemoryError: Container killed`** riski; heap’i limitin **%60–70**’i civarı hedefle.
    

---

### 295) API mimari türleri

**REST**

- Artı: Basit, yaygın, HTTP ekosistemi güçlü.
    
- Eksi: Over/under-fetch; versiyonlama ve sözleşme disiplini şart.
    
- Kullan: Genel amaçlı harici API.
    

**gRPC**

- Artı: **Protobuf** ile hızlı/kompakt, HTTP/2, streaming.
    
- Eksi: Tarayıcı doğrudan sınırlı; genelde **gateway** lazım.
    
- Kullan: Mikroservis-içi, düşük latency, yüksek throughput.
    

**GraphQL**

- Artı: Tek endpoint, **istemci istediği alanı** alır; mobil/çok ekran için harika.
    
- Eksi: N+1, caching/policy zor; gateway ve schema governance şart.
    
- Kullan: Zengin istemci ihtiyaçları, farklı view’lar.
    

**SOAP**

- Artı: WS-* ile kurumsal güvenlik/transaction standartları.
    
- Eksi: Ağır; modern web için hantaldır.
    
- Kullan: Miras sistemler, zorunlu entegrasyonlar.
    

**MQ/Event-Driven**

- Artı: Gevşek bağ, **backpressure**, retry/DLQ; offline toleransı.
    
- Eksi: Teslim garantileri, sıraya alma ve **veri tutarlılığı** yönetimi.
    
- Kullan: Asenkron süreçler, entegrasyon, audit akışları.
    

**Kısa karar ağacı:**

- **İç servis ↔ iç servis, performans kritik** → gRPC
    
- **Dış dünya/mobil/web** → REST veya GraphQL
    
- **Asenkron iş akışı** → Kafka/RabbitMQ
    
- **Kurumsal legacy** → SOAP kaçınılmaz olabilir
    

---

### 296) PostgreSQL’de paralel sorgu nasıl çalışır?

**Çalışma mantığı:** Planner uygun görürse **Parallel Seq Scan / Parallel Index Scan** planı üretir, **Gather/Gather Merge** düğümüyle worker sonuçlarını birleştirir.  
**Paralelleşebilenler:** Büyük `SELECT`ler, `JOIN`ler, `AGG`ler; `PARALLEL SAFE` fonksiyonlar.  
**Paraleli engelleyenler:** Küçük tablolar (kâr etmiyor), `PARALLEL UNSAFE` fonksiyonlar, belirli cursor/snapshot durumları.

**Kritik ayarlar:**

- `max_worker_processes` (toplam işçi üst sınırı)
    
- `max_parallel_workers` (paralel worker üst sınırı)
    
- `max_parallel_workers_per_gather` (tek sorgu için max worker)
    
- `min_parallel_table_scan_size`, `min_parallel_index_scan_size` (paralel kullanmak için alt sınır)
    
- `parallel_leader_participation` (leader da çalışsın mı)
    
- Cost tuning: `parallel_setup_cost`, `parallel_tuple_cost`
    

**Hızlı deneme:**

```sql
SET max_parallel_workers_per_gather = 4;
SET max_parallel_workers = 8;
SET max_worker_processes = 8;

EXPLAIN (ANALYZE, BUFFERS)
SELECT sum(t.amount)
FROM big_table t
JOIN big_lookup l ON t.fk = l.id
WHERE t.created_at >= now() - interval '30 days';
-- Plan'da 'Gather' ve 'Parallel Seq Scan' görmelisin.
```

**İpuçları:**

- Büyük taramalar için **istatikler güncel** olsun (`ANALYZE`).
    
- `PARALLEL SAFE` fonksiyonlar yaz (immutable/pure).
    
- Columnar/OLAP motorları (ClickHouse, Citus, etc.) daha agresif paralellik sunar; ihtiyaca göre mimariyi seç.
    

---

### 297) MapStruct `expression`

**Amaç:** Sıradan alan eşlemesi yetmeyince **inline Java** ifadesi yazmak.

**Basit kullanım:**

```java
@Mapping(target = "fullName",
         expression = "java(src.getFirstName() + \" \" + src.getLastName())")
Target map(Source src);
```

**Helper ile (önerilir):**

```java
@Mapper(uses = NameHelper.class)
interface UserMapper {
  @Mapping(target="fullName",
           qualifiedByName="joinFullName")
  Target map(Source src);
}

class NameHelper {
  @Named("joinFullName")
  String fullName(Source s) {
    return (s.getFirstName() + " " + s.getLastName()).trim();
  }
}
```

**Neden helper?** Test edilebilirlik, tekrar kullanım, karmaşık mantığın mapper’den izole edilmesi.

**Diğer faydalılar:**

- `constant = "TR"` sabit atama
    
- `defaultExpression = "java(Instant.now())"`
    
- `nullValuePropertyMappingStrategy = IGNORE` (patch mantığı)
    
- `@AfterMapping` ile post-process.
    

---

### 298) Asenkron 5 servis çağrısını tek yerde toplamak

**Çekirdek fikir:** `CompletableFuture.supplyAsync` + `allOf` + **özel `Executor`** + **timeout/exception** yönetimi.

```java
var exec = Executors.newFixedThreadPool(8, r -> {
  var t = new Thread(r); t.setName("io-pool-%d".formatted(t.threadId())); t.setDaemon(true); return t;
});

CompletableFuture<ResultA> f1 = supplyAsync(() -> s1.call(), exec).orTimeout(2, SECONDS);
CompletableFuture<ResultB> f2 = supplyAsync(() -> s2.call(), exec).orTimeout(2, SECONDS);
CompletableFuture<ResultC> f3 = supplyAsync(() -> s3.call(), exec).orTimeout(2, SECONDS);
CompletableFuture<ResultD> f4 = supplyAsync(() -> s4.call(), exec).orTimeout(2, SECONDS);
CompletableFuture<ResultE> f5 = supplyAsync(() -> s5.call(), exec).orTimeout(2, SECONDS);

CompletableFuture<Void> all = allOf(f1,f2,f3,f4,f5);

Aggregated res = all.handle((v, ex) -> {
  // Centralized hata-toplama
  var a = safeJoin(f1); var b = safeJoin(f2); var c = safeJoin(f3);
  var d = safeJoin(f4); var e = safeJoin(f5);
  return aggregate(a,b,c,d,e);
}).join();
```

```java
static <T> T safeJoin(CompletableFuture<T> f) {
  try { return f.join(); } catch (CompletionException ce) { /* log + fallback */ return null; }
}
```

**Notlar:**

- I/O ağırlıklı ise thread sayısını çekinmeden artır; CPU-bound ise `ForkJoinPool`’u (varsayılan) tart.
    
- Gelişmiş hataya dayanıklılık için **Resilience4j** `Bulkhead/Retry/TimeLimiter` dekoratörleri ile sar.
    
- Spring `WebClient` kullanıyorsan `Mono.zip(f1,f2,...)` aynı işi reaktif tarzda yapar.
    

---

### 299) Outbox Pattern

**Sorun:** DB’ye yaz + mesaj kuyruğuna yayın = iki kaynak → **tutarsızlık**.  
**Çözüm:** İşlemi tek transaction’da **DB + Outbox** tablosuna yaz. Ayrı bir publisher **Outbox’u okuyup** kuyruk/kafkaya **en az bir kez** (at-least-once) yollar.

**Şema örneği:**

```sql
CREATE TABLE outbox (
  id           UUID PRIMARY KEY,
  aggregate_id UUID NOT NULL,
  type         TEXT NOT NULL,          -- event type
  payload      JSONB NOT NULL,
  created_at   TIMESTAMPTZ NOT NULL DEFAULT now(),
  published_at TIMESTAMPTZ,
  status       TEXT NOT NULL DEFAULT 'NEW', -- NEW|SENT|FAILED
  UNIQUE (id)
);
```

**Akış:**

1. Uygulama transaction’ında domain yazımı + `INSERT INTO outbox (...)`
    
2. Publisher (job/worker) `NEW` kayıtları **idempotent** şekilde okur, kuyruğa yollar.
    
3. Başarılıysa `status='SENT', published_at=now()` günceller; hata varsa `RETRY`/DLQ.
    

**İpuçları:**

- Publisher **tam idempotent** olmalı (aynı event tekrar gelirse **no-op**).
    
- Alternatif: **CDC** (Debezium) → WAL’dan okur, uygulama kodu **sadeleşir**.
    
- Outbox tablosunu **partisyonla/temizle** (TTL/archival).
    

---

### 300) Sonsuz döngü ne zaman tercih edilir (ve nasıl güvenli yazılır)?

**Kullanım yerleri:** Queue consumer, dosya/dizin watcher, daemon görev, health/probe üreticisi.

**Güvenli döngü şablonu:**

```java
class Worker implements AutoCloseable {
  private final AtomicBoolean running = new AtomicBoolean(true);

  public void start() {
    while (running.get()) {
      try {
        processOneBatch();                 // iş
        if (noWork()) LockSupport.parkNanos(MILLISECONDS.toNanos(100)); // backoff
      } catch (TransientException e) {
        LockSupport.parkNanos(MILLISECONDS.toNanos(200)); // jitter/backoff
      } catch (Throwable t) {
        // log & metric; kara delik olmasın
      }
      if (Thread.interrupted()) running.set(false); // cooperative stop
    }
  }

  public void stop() { running.set(false); }
  public void close() { stop(); }
}
```

**Altın kurallar:**

- **Stop sinyali** (volatile/AtomicBoolean).
    
- **Backoff** (sabit değil, jitter’lı) → CPU yakma.
    
- **Metrics & health**: iteration süresi, hata sayısı, queue lag.
    
- **Kapatma kancaları**: `PreDestroy`/`close()`.
    

**Alternatifler:** `ScheduledExecutorService`, reaktif akış (Project Reactor), K8s CronJob/Jobs.

---

### 301) OLTP, OLAP, Data Warehouse

**OLTP (işlemsel)**

- Kısa, sık; **INSERT/UPDATE/SELECT by PK**.
    
- Normalleştirilmiş şema; güçlü **ACID**.
    
- Örnek: Sipariş oluşturma, ödeme.
    

**OLAP (analitik)**

- Büyük taramalar, gruplamalar; **read-heavy**.
    
- Denormalize/star şema; genelde kolon bazlı depolar.
    
- Örnek: Aylık satış analizi, kohort raporları.
    

**Data Warehouse (DWH)**

- Çok kaynaktan veri **entegrasyonu**; tarihsel tutma.
    
- Şema: **Star/Snowflake**; ETL/ELT ile yüklenir.
    
- Motorlar: BigQuery, Snowflake, Redshift, ClickHouse, Druid…
    

**Mimarî notlar:**

- OLTP → DWH akışı: **Change Data Capture** (CDC) ile gerçek-zamanlı besleme.
    
- Sıcak raporlar için **materialized view**/**rollup tablolar**.
    
- Bütçe: Sorgu başına fiyatlandırılan sistemlerde **partisyon + cluster key** şart.
    

---

### 302) Circuit Breaker

**Durumlar:**

- **Closed:** Çağrılar normal; hata/slow oranı eşik aşarsa **Open**.
    
- **Open:** Çağrıları **kestir**; **waitDurationInOpenState** dolunca **Half-Open**.
    
- **Half-Open:** Sınırlı sayıda deneme; başarılıysa **Closed**, yoksa **Open**’a geri.
    

**Resilience4j ile kullanım (Java):**

```java
var cbConfig = CircuitBreakerConfig.custom()
  .failureRateThreshold(50)                // %
  .slowCallRateThreshold(50)               // %
  .slowCallDurationThreshold(Duration.ofSeconds(2))
  .slidingWindowType(COUNT_BASED)
  .slidingWindowSize(100)
  .minimumNumberOfCalls(50)
  .waitDurationInOpenState(Duration.ofSeconds(10))
  .permittedNumberOfCallsInHalfOpenState(5)
  .recordExceptions(SocketTimeoutException.class, IOException.class)
  .build();

var cb = CircuitBreaker.of("downstreamA", cbConfig);
Supplier<Response> guarded = CircuitBreaker
  .decorateSupplier(cb, () -> client.call());

// Opsiyonel: Retry/TimeLimiter/Bulkhead ile kombinle
var retry = Retry.ofDefaults("downstreamA");
var decorated = Retry.decorateSupplier(retry, guarded);

Response res = Try.ofSupplier(decorated)
                  .getOrElseGet(ex -> fallbackResponse());
```

**İpuçları:**

- **Slow-call** oranını da izle; sadece “exception” değil.
    
- **Fallback** hafif ve hızlı olmalı (cache/son bilinen iyi değer).
    
- Breaker metriklerini dışa at: **Micrometer + Prometheus**.
