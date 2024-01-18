# ObserverPattern-MVP-Based-User-Interface
Basit bir Health ve Mana sistemini içeren ve MVP tabanlı bir arayüze sahip bir FPS oyun prototipini içeren repo'dur.<br>

---Observer Classes---<br>
<b>IObserver.cs =></b> Subscriber sınıflar bu interface'i implemente ederek OnNotify methoduna erişim sağlarlar.<br>
<b>Subject.cs =></b> Event'leri fire edecek sınıflar bu sınıfı miras alarak AddObserver, RemoveObserver ve NotifyObservers methodlarına erişim sağlarlar. <br><br>

---MagicCircle Classes---<br>
Magic Circle'lar oyun içerisinde player'ın health ve mana özelliklerine etki eden alanlardır. Player bir Magic Circle içerisine girdiğinde etki başlar.<br>
<b>ICircle.cs =></b> Tüm Magic Circle'lar bu interface'i implemente ederek bazı ortak özellikler ve methodlara sahip olurlar. GetCalculatedAmount methodu bu alanın nasıl bir etki oluşturacağı datasını döndürür.<br>
<b>DamageCircle.cs =></b> Player'ın health'ini azaltan bir alan tipidir.<br>
<b>HealCircle.cs =></b> Player'ın health'ini artıran bir alan tipidir.<br>
<b>ManaCircle.cs =></b> Player'ın mana'sını azaltan bir alan tipidir.<br><br>

---Player Classes---<br>
<b>PlayerMovement.cs =></b> Bu FPS Player'ının movement işlemlerini içeren bir sınıftır. Character Controller ile iletişime geçerek oyuncuyu hareket ettirir.<br>
<b>PlayerStats.cs =></b> Oyuncu health ve mana değerlerinin tutulduğu ve güncellendiği sınıftır. ReceiveInteraction ve PlayerMovement sınıflarına Subscribe olur ve IObserver interface'ini implemente ederek OnNotify methodu üzerinden health ve mana değişimlerinden haberdar olur.<br>
<b>ReceiveInteraction.cs =></b> Player Character collider'ı Magic Circle Collider'larına temas ettiğinde, ICircle interface'i üzerinden Magic Circle'ın GetCalculatedAmount methoduna erişir ve PlayerStats'a değişim isteğini Event fire ederek iletir.<br><br>

---UI Classes---<br>
<b>PlayerBasicDataUI.cs =></b> Observer Pattern'e farklı bir örnek olarak, bu sınıf Subject'ine Observer Class'ları üzreinden değil, onun yerine Unity Action üzerinden subscribe olur. Bu örnekte PlayerStats'ın Action'larına subscribe olarak health ve mana değişim yaşadığında UI güncellenir.<br>
