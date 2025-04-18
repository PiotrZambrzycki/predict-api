
# Predict API

Serwis API w Pythonie uruchamiany w kontenerze Docker, który zwraca predykcję na podstawie sumy dwóch liczb.

## Funkcjonalność

Endpoint `/api/v1.0/predict` przyjmuje dwie liczby (`num1` i `num2`) jako parametry.  
Jeśli suma tych liczb jest większa niż 5.8, zwraca prediction: 1, w przeciwnym razie prediction: 0.  
Jeśli użytkownik nie poda którejś liczby, zostanie przyjęte 0.

---

## Jak uruchomić?

### 1. Zbuduj obraz Dockera

W folderze z plikami projektu uruchom w terminalu:

docker build -t projekty .



### 2. Uruchom kontener

docker run -d -p 8000:8080 projekty



### 3. Testowanie API

Otwórz przeglądarkę lub narzędzie typu Postman i wywołaj:

http://localhost:8000/api/v1.0/predict?num1=3&num2=4



**Przykładowe odpowiedzi:**

- `http://localhost:8000/api/v1.0/predict?num1=3&num2=4`  
{
"prediction": 1,
"features": {
"num1": 3.0,
"num2": 4.0,
"sum": 7.0
}
}


- `http://localhost:8000/api/v1.0/predict?num1=2&num2=2`  
{
"prediction": 0,
"features": {
"num1": 2.0,
"num2": 2.0,
"sum": 4.0
}
}



- `http://localhost:8000/api/v1.0/predict?num1=4`  
{
"prediction": 0,
"features": {
"num1": 4.0,
"num2": 0.0,
"sum": 4.0
}
}



---

## Informacje dodatkowe

- Jeśli nie podasz którejś liczby, zostanie przyjęte 0.
- Port 8000 na komputerze jest przekierowany do portu 8080 w kontenerze.


---

## Autor

Piotr Zambrzycki 
141303