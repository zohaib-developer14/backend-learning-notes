# Verification vs Authentication vs Authorization

## Core Points

1. **Verification** contact ownership confirm karti hai (email ya phone OTP se prove karna ke yeh waqai user ka hai).
2. **Authentication (AuthN)** identity prove karta hai (email + password match? JWT valid?).
3. **Authorization (AuthZ)** permissions control karta hai (user kya kar sakta hai? admin ya normal user?).
4. Verification trust layer hai, Authentication identity layer hai, Authorization access control layer hai.
5. Secure systems mein yeh teen layers alag hoti hain lekin mil kar kaam karti hain.

---

## Simple Flow Example

Register → Verify Email → Login (Authenticate) → Access Control (Authorize)

---

## Faida

* Clear architecture design
* Better security model
* Access control properly manage hota hai
* Sensitive systems mein misuse risk kam hota hai

---

## Technical Questions (With Answers)

**Q1:** Kya verification ke bina authentication allow karna safe hai?

**Answer:** Technically possible hai, lekin fake emails aur spam accounts ka risk barh jata hai.

**Q2:** Agar user authenticated hai lekin role change ho gaya ho, to kya authorization check har request par hona chahiye?

**Answer:** Haan. Authorization middleware har protected route par role check karega, warna old token se privilege misuse ho sakta hai.
