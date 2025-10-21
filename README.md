# Delivery Dash Game

**Delivery Dash** is a simple 2D Unity game created as a course project.
You play as a delivery driver racing around town to **pick up packages** and **deliver them to customers** — but watch out! Collisions slow you down, and you’ll need to make use of **boosters** to keep your deliveries speedy and efficient.

---

## Gameplay Overview

* **Objective:**
  Pick up packages from marked spots and deliver them to customers spread around the map.

* **Controls:**

  | Key | Action        |
  | --- | ------------- |
  | W   | Move Forward  |
  | S   | Move Backward |
  | A   | Turn Left     |
  | D   | Turn Right    |

* **Boosters:**
  Driving over a Booster temporarily increases your speed — but the boost wears off when you hit an obstacle!

---

## Core Scripts

### `Driver.cs`

Handles vehicle movement, rotation, and booster behavior.

**Key Features:**

* Controls movement using `WASD` keys.
* Increases speed when hitting a **Booster** (`Tag: "Booster"`).
* Displays a UI message when boosted (`TMP_Text boostText`).
* Resets to normal speed upon collision with any object.

**Code Highlights:**

```csharp
if (other.CompareTag("Booster") && !isBoosted)
{
    movementSpeed = boostSpeed;
    boostText.gameObject.SetActive(true);
    isBoosted = true;
    Destroy(other.gameObject);
}
```

---

### `Delivery.cs`

Manages package pickup and delivery interactions.

**Key Features:**

* Detects collision with `Package` and `Customer` objects.
* Plays a particle effect when picking up or delivering.
* Destroys package after a short delay to simulate pickup.
* Prevents picking up multiple packages at once.

**Code Highlights:**

```csharp
if (collision.CompareTag("Package") && !hasPackage)
{
    Debug.Log("Item Picked Up!");
    hasPackage = true;
    GetComponent<ParticleSystem>().Play();
    Destroy(collision.gameObject, delay);
}
```
## Technologies Used

* **Engine:** Unity
* **Language:** C#
* **UI Framework:** TextMeshPro (TMP)
* **Input System:** Unity Input System

---

## Author

**Ahmad Sajid Kabir**
Game Development Course Project — *Delivery Dash (2025)*

---

