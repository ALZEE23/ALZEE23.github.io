# Unity Component Implementation

Dokumentasi ini berisi penjelasan dan contoh implementasi component di Unity.

## 📋 Daftar Component

- [`/child-component`](#-child-component)

  > Implementasi untuk menggunakan atau memanipulasi child component.

- [`/rigidbody`](./save-system/)

  > Sistem save dan load data game menggunakan ScriptableObjects.

- [`/event-system`](./event-system/)

  > Implementasi event system untuk komunikasi antar component.

- [`/singleton`](./singleton/)

  > Pattern singleton untuk manager dan service classes.

- [`/state-machine`](./state-machine/)

  > Implementasi state machine untuk behavior management.

## 📝 Get Child Component

Ini contoh kalo mau menggunakan atau mengganti component child tapi dari script yang ada di parent ini berguna banget apalagi kalo child nya ada banyak

- Contoh untuk Mengambil semua posisi child dalam sebuah parent lalu mengganti layer nya saay di click mouse

```csharp
public class ExampleComponent : MonoBehaviour
{
    private int defaultLayer;
    public int outlineLayer = 10; // ini adalah cara mengambil layer namun dengan urutan nya
    private Transform[] allChildren; // buat sebuah array list kosong dimana untuk menampung semua component child

    private void Start()
    {
        defaultLayer = gameObject.layer; // setiap gameobject pasti memiliki layer nah dengan begini maka gamobject yang memiliki script ini akan di ambil layer untuk disimpan
        allChildren = GetComponentsInChildren<Transform>(true); // saat game dimulai maka getcomponents in children akan bekerja dan mengambil semua child dengan true sebagai trigger nya
    }

    private void OnMouseEnter()
    {
        foreach (Transform child in allChildren) // lalu kita gunakan for loop untuk mengganti semua component yang ada di dalam array all children karena kalo gak di for loop gini nanti cuman index 0 doang yang ke ganti
        {
            child.gameObject.layer = outlineLayer; // panggil si variable for loop nya dan ini harus di specified yaitu type nya transform karena all children itu transform
        }
    }

    private void OnMouseExit()
    {
        foreach (Transform child in allChildren)
        {
            child.gameObject.layer = defaultLayer;
        }
    }
}
```

- Contoh Untuk Membuat sebuah Card Slot Manager yang dimana akan menampilkan data atau prefab ke child sebuah parent

```csharp
public class CardSlotManager : Monobehaviour
{
    public List<Card> cardData;
    public Transform parentSlot;


    void Start(){
        foreach ( Card cards in cardData ){
          Debug.Log("Name" + cards.name);
        }

        CardInstantiate();
    }

    public CardInstantiate(){
      foreach ( Card cards in cardData ){
        Instantiate(cards.cardPrefab, parentSlot.transform, Quaternion.identity, parentSlot)
      }
    }
}

public class Card {
    public string name;
    public GameObject cardPrefab;
    public string id;
}
```

## 🚀 Contoh Implementasi

Setiap folder memiliki:

- Penjelasan konsep dasar
- Sample code dan use cases
- Tips optimasi
- Common pitfalls yang perlu dihindari

---

Dokumentasi ini akan terus diperbarui dengan pattern dan implementasi baru.
