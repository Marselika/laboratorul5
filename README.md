# laboratorul5
# Raport Tehnic: Implementarea Sistemului de Autentificare în Laravel
## Universitatea USM
### Disciplina: Dezvoltare Web
### Student: Iatco Marcel

## 1. Introducere

Acest proiect prezintă implementarea unui sistem complex de autentificare și autorizare utilizând framework-ul Laravel. Scopul principal al proiectului este dezvoltarea unei aplicații web sigure cu management al utilizatorilor și control al accesului bazat pe roluri.

## 2. Tehnologii Utilizate

- Laravel 10
- PHP 8
- MySQL
- HTML/CSS
- Laravel Fortify pentru autentificare

## 3. Funcționalități Implementate

### 3.1 Sistem de Autentificare
- Înregistrare utilizatori noi
- Autentificare utilizatori existenți
- Deconectare
- Protecție împotriva atacurilor CSRF
- Validare date de intrare

### 3.2 Sistem de Roluri
- Administrator
- Utilizator standard

### 3.3 Panou de Control
- Dashboard personalizat pentru fiecare utilizator
- Interfață administrativă pentru gestionarea utilizatorilor
- Vizualizare informații utilizator

## 4. Structura Proiectului

### 4.1 Baza de Date
```sql
users (
    id,
    name,
    email,
    password,
    role ENUM('admin', 'user'),
    created_at,
    updated_at
)
```

### 4.2 Controllers
```php
UserController
- index() - listă utilizatori
- showDashboard() - dashboard personal
```

## 5. Răspunsuri la Întrebările Cheie

### 5.1 Soluții de Autentificare în Laravel
Laravel oferă mai multe soluții integrate pentru autentificare:
1. **Laravel Breeze** - soluție minimală, perfectă pentru proiecte mici
2. **Laravel Fortify** (utilizată în proiect) - backend headless pentru autentificare
3. **Laravel Jetstream** - soluție completă cu funcționalități avansate
4. **Laravel Sanctum** - pentru autentificare API

### 5.2 Metode de Autentificare Implementate
În proiectul nostru am implementat:
1. **Autentificare bazată pe sesiune**
   - Stocare în baza de date
   - Regenerare token la login
   - Invalidare sesiune la logout

2. **Autentificare prin formular**
   - Validare email/parolă
   - Hashing parole
   - Protecție împotriva atacurilor de tip brute force

### 5.3 Diferența între Autentificare și Autorizare

**Autentificare**:
- Verifică identitatea utilizatorului
- Procesul de login/register
- Răspunde la întrebarea "Cine ești?"

**Autorizare**:
- Verifică drepturile utilizatorului
- Implementată prin sistem de roluri
- Răspunde la întrebarea "Ce ai voie să faci?"

### 5.4 Protecția CSRF în Laravel
În proiectul nostru, protecția CSRF este implementată prin:
1. **Token CSRF**
   ```php
   @csrf
   ```
   în toate formularele

2. **Middleware VerifyCsrfToken**
   - Verifică automat token-ul pentru toate cererile POST
   - Previne atacurile CSRF

3. **Regenerare Token**
   - La login
   - La logout
   - La schimbarea sesiunii

## 6. Securitate

Proiectul implementează următoarele măsuri de securitate:
1. Hashing parole cu bcrypt
2. Validare date de intrare
3. Protecție CSRF
4. Middleware de autentificare
5. Sistem de roluri și permisiuni

## 7. Concluzii

Proiectul demonstrează implementarea cu succes a unui sistem de autentificare și autorizare robust în Laravel, oferind:
- Securitate ridicată
- Managementul eficient al utilizatorilor
- Control granular al accesului
- Interfață intuitivă
