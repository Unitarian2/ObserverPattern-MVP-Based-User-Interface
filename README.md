# ObserverPattern-MVP-Based-User-Interface
Basit bir Health ve Mana sistemini içeren ve MVP tabanlı bir arayüze sahip bir FPS oyun prototipini içeren repo'dur.<br>

---Observer Classes---<br>
IObserver.cs => Subscriber sınıflar bu interface'i implemente ederek OnNotify methoduna erişim sağlarlar.
Subject.cs => Event'leri fire edecek sınıflar bu sınıfı miras alarak AddObserver, RemoveObserver ve NotifyObservers methodlarına erişim sağlarlar. 

---MagicCircle Classes---<br>
Magic Circle'lar oyun içerisinde player'ın health ve mana özelliklerine etki eden alanlardır. Player bir Magic Circle içerisine girdiğinde etki başlar.
ICircle.cs => Tüm Magic Circle'lar bu interface'i implemente ederek bazı ortak özellikler ve methodlara sahip olurlar. GetCalculatedAmount methodu bu alanın nasıl bir etki oluşturacağı datasını döndürür.
DamageCircle.cs => Player'ın health'ini azaltan bir alan tipidir.
HealCircle.cs => Player'ın health'ini artıran bir alan tipidir.
ManaCircle.cs => Player'ın mana'sını azaltan bir alan tipidir.

---Player Classes---<br>
PlayerMovement.cs => Bu FPS Player'ının movement işlemlerini içeren bir sınıftır. Character Controller ile iletişime geçerek oyuncuyu hareket ettirir.
PlayerStats.cs => Oyuncu health ve mana değerlerinin tutulduğu ve güncellendiği sınıftır. ReceiveInteraction ve PlayerMovement sınıflarına Subscribe olur ve IObserver interface'ini implemente ederek OnNotify methodu üzerinden health ve mana değişimlerinden haberdar olur.
ReceiveInteraction.cs => Player Character collider'ı Magic Circle Collider'larına temas ettiğinde, ICircle interface'i üzerinden Magic Circle'ın GetCalculatedAmount methoduna erişir ve PlayerStats'a değişim isteğini Event fire ederek iletir.
