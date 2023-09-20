Zadeklaruj tablicę 10 liczb rzeczywistych i wypełnij ją pierwiastkami jej indeksów.
public class Main {
    public static void main(String[] args) {
        double[] tablica = new double[10];

        for (int i = 0; i < tablica.length; i++) {
            tablica[i] = Math.sqrt(i);
        }

        // Wyświetlenie zawartości tablicy
        System.out.println("Tablica pierwiastków indeksów:");
        for (int i = 0; i < tablica.length; i++) {
            System.out.println("tablica[" + i + "] = " + tablica[i]);
        }
    }
}



Zadeklaruj tablicę z liczbami całkowitymi i wstaw do niej 100 liczb losowych z zakresu od 1 do 100.

 

Zadeklaruj dwie kolekcje i wypełnij je wartościami z tablicy. Do jednej wstaw liczby parzyste, a do drugiej nieparzyste.

 

Podaj, ile różnych liczb wylosowano.

import java.util.ArrayList;
import java.util.HashSet;
import java.util.Random;
import java.util.Set;

public class Main {
    public static void main(String[] args) {
        // Deklaracja i inicjalizacja tablicy z losowymi liczbami całkowitymi
        int[] tablica = new int[100];
        Random random = new Random();

        for (int i = 0; i < tablica.length; i++) {
            tablica[i] = random.nextInt(100) + 1; // Losowanie liczby z zakresu 1-100
        }

        // Deklaracja dwóch kolekcji dla liczb parzystych i nieparzystych
        ArrayList<Integer> liczbyParzyste = new ArrayList<>();
        ArrayList<Integer> liczbyNieparzyste = new ArrayList<>();

        // Wypełnienie kolekcji liczbami parzystymi i nieparzystymi
        for (int liczba : tablica) {
            if (liczba % 2 == 0) {
                liczbyParzyste.add(liczba);
            } else {
                liczbyNieparzyste.add(liczba);
            }
        }

        // Utworzenie zbioru HashSet do zliczania unikalnych liczb
        Set<Integer> unikalneLiczby = new HashSet<>();
        for (int liczba : tablica) {
            unikalneLiczby.add(liczba);
        }

        // Wyświetlenie wyników
        System.out.println("Liczby parzyste: " + liczbyParzyste);
        System.out.println("Liczby nieparzyste: " + liczbyNieparzyste);
        System.out.println("Ilość różnych liczb wylosowanych: " + unikalneLiczby.size());
    }
}



Wykorzystaj tablicę z zadania 3. z wylosowanymi wartościami. Posortuj tablicę. Znajdź medianę (wartość środkową tablicy), dominantę (wartość najczęściej występującą w tablicy) i wartość średnią wartości zapisanych w tablicy.

import java.util.Arrays;
import java.util.HashMap;
import java.util.Map;

public class Main {
    public static void main(String[] args) {
        // Tablica z wylosowanymi wartościami
        int[] tablica = {/* tutaj umieść swoją tablicę z poprzedniego zadania */};

        // Sortowanie tablicy
        Arrays.sort(tablica);

        // Mediana
        double mediana;
        if (tablica.length % 2 == 0) {
            int srodkowy1 = tablica[(tablica.length - 1) / 2];
            int srodkowy2 = tablica[tablica.length / 2];
            mediana = (srodkowy1 + srodkowy2) / 2.0;
        } else {
            mediana = tablica[tablica.length / 2];
        }

        // Dominanta
        Map<Integer, Integer> liczniki = new HashMap<>();
        int maxCzestosc = 0;
        int dominanta = -1;

        for (int liczba : tablica) {
            int czestosc = liczniki.getOrDefault(liczba, 0) + 1;
            liczniki.put(liczba, czestosc);

            if (czestosc > maxCzestosc) {
                maxCzestosc = czestosc;
                dominanta = liczba;
            }
        }

        // Wartość średnia
        int suma = 0;
        for (int liczba : tablica) {
            suma += liczba;
        }
        double srednia = (double) suma / tablica.length;

        // Wyświetlenie wyników
        System.out.println("Posortowana tablica: " + Arrays.toString(tablica));
        System.out.println("Mediana: " + mediana);
        System.out.println("Dominanta: " + dominanta);
        System.out.println("Wartość średnia: " + srednia);
    }
}




Wygeneruj tablicę liczb pierwszych mniejszych od 1000. Wykorzystaj do tego sito Eratostenesa. Wypisz wszystkie liczby pierwsze z zakresu od x do y, gdzie x0 ix,y <1000.

public class Main {
    public static void main(String[] args) {
        int max = 1000; // Maksymalna wartość, do której generujemy liczby pierwsze
        boolean[] isPrime = new boolean[max]; // Tablica, w której będziemy śledzić, czy liczba jest pierwsza

        // Inicjalizacja tablicy jako "true" - zakładamy, że wszystkie liczby są pierwsze
        for (int i = 2; i < max; i++) {
            isPrime[i] = true;
        }

        // Sito Eratostenesa - oznaczamy wielokrotności liczb jako "false"
        for (int i = 2; i * i < max; i++) {
            if (isPrime[i]) {
                for (int j = i * i; j < max; j += i) {
                    isPrime[j] = false;
                }
            }
        }

        // Zakres x i y
        int x = 100;
        int y = 200;

        // Wyświetlenie liczb pierwszych z zakresu od x do y
        System.out.println("Liczby pierwsze z zakresu od " + x + " do " + y + ":");
        for (int i = Math.max(x, 2); i < Math.min(y, max); i++) {
            if (isPrime[i]) {
                System.out.println(i);
            }
        }
    }
}



Wypisz na ekranie wszystkie liczby dodatnie dwucyfrowe parzyste. Liczby oddziel znakiem spacji.

public class Main {
    public static void main(String[] args) {
        for (int i = 10; i <= 99; i += 2) {
            System.out.print(i + " ");
        }
    }
}




Wczytaj słowo z klawiatury i sprawdź, czy jest palindromem, czyli czytane od początku do końca i od końca do początku ma takie samo brzmienie.


import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Wprowadź słowo: ");
        String slowo = scanner.nextLine();
        scanner.close();

        if (jestPalindromem(slowo)) {
            System.out.println(slowo + " jest palindromem.");
        } else {
            System.out.println(slowo + " nie jest palindromem.");
        }
    }

    public static boolean jestPalindromem(String slowo) {
        // Usunięcie białych znaków i zmiana na małe litery
        slowo = slowo.replaceAll("\\s", "").toLowerCase();

        int dlugosc = slowo.length();
        for (int i = 0; i < dlugosc / 2; i++) {
            if (slowo.charAt(i) != slowo.charAt(dlugosc - 1 - i)) {
                return false; // Jeśli znaki nie pasują, to to nie jest palindrom
            }
        }
        return true; // Jeśli przejdziemy przez pętlę, to jest to palindrom
    }
}



Znajdź dla danej liczby najbliższą jej liczbę palindromiczną (czytana od początku jest taka sama jak czytana od końca). Dla liczby 1015 najbliższą liczbą palindromiczną jest liczba 1001.

public class Main {
    public static void main(String[] args) {
        long liczba = 1015; // Twoja liczba

        long najblizszaPalindromiczna = znajdzNajblizszaPalindromiczna(liczba);
        System.out.println("Najbliższa liczba palindromiczna dla " + liczba + " to " + najblizszaPalindromiczna);
    }

    public static long znajdzNajblizszaPalindromiczna(long liczba) {
        while (true) {
            if (czyJestPalindromem(liczba)) {
                return liczba;
            }
            liczba++;
        }
    }

    public static boolean czyJestPalindromem(long liczba) {
        String liczbaStr = String.valueOf(liczba);
        int dlugosc = liczbaStr.length();
        for (int i = 0; i < dlugosc / 2; i++) {
            if (liczbaStr.charAt(i) != liczbaStr.charAt(dlugosc - 1 - i)) {
                return false;
            }
        }
        return true;
    }
}


Wczytaj słowo z klawiatury i zaszyfruj je szyfrem Cezara z kluczem 3. Szyfr Cezara polega na przesunięciu każdej litery alfabetu w prawo o klucz.



import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Wprowadź słowo do zaszyfrowania: ");
        String slowo = scanner.nextLine();
        scanner.close();

        int klucz = 3; // Klucz szyfru Cezara

        String zaszyfrowaneSłowo = szyfrujCezarem(slowo, klucz);
        System.out.println("Zaszyfrowane słowo: " + zaszyfrowaneSłowo);
    }

    public static String szyfrujCezarem(String slowo, int klucz) {
        StringBuilder zaszyfrowaneSlowo = new StringBuilder();

        for (int i = 0; i < slowo.length(); i++) {
            char znak = slowo.charAt(i);

            if (Character.isLetter(znak)) {
                char poczatekAlfabetu = Character.isUpperCase(znak) ? 'A' : 'a';
                int pozycja = znak - poczatekAlfabetu;
                int nowaPozycja = (pozycja + klucz) % 26;
                char nowyZnak = (char) (poczatekAlfabetu + nowaPozycja);
                zaszyfrowaneSlowo.append(nowyZnak);
            } else {
                zaszyfrowaneSlowo.append(znak); // Jeśli znak nie jest literą, pozostaw go bez zmian
            }
        }

        return zaszyfrowaneSlowo.toString();
    }
}


Wczytaj dwa słowa i sprawdź, czy są one dla siebie anagramami, czyli składają się z tych samych liter w takiej samej liczbie.

import java.util.Arrays;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Wprowadź pierwszy wyraz: ");
        String wyraz1 = scanner.nextLine();
        System.out.print("Wprowadź drugi wyraz: ");
        String wyraz2 = scanner.nextLine();
        scanner.close();

        if (czyAnagramy(wyraz1, wyraz2)) {
            System.out.println("Podane wyrazy są anagramami.");
        } else {
            System.out.println("Podane wyrazy nie są anagramami.");
        }
    }

    public static boolean czyAnagramy(String wyraz1, String wyraz2) {
        // Usunięcie białych znaków i zamiana liter na małe
        wyraz1 = wyraz1.replaceAll("\\s", "").toLowerCase();
        wyraz2 = wyraz2.replaceAll("\\s", "").toLowerCase();

        // Jeśli długości wyrazów są różne, to na pewno nie są anagramami
        if (wyraz1.length() != wyraz2.length()) {
            return false;
        }

        // Konwersja wyrazów na tablice znaków i ich sortowanie
        char[] tablicaWyraz1 = wyraz1.toCharArray();
        char[] tablicaWyraz2 = wyraz2.toCharArray();
        Arrays.sort(tablicaWyraz1);
        Arrays.sort(tablicaWyraz2);

        // Porównanie posortowanych tablic znaków
        return Arrays.equals(tablicaWyraz1, tablicaWyraz2);
    }
}



Napisz program obliczający sumę silni cyfr z liczby.

import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Wprowadź liczbę: ");
        int liczba = scanner.nextInt();
        scanner.close();

        int sumaSilniCyfr = obliczSumeSilniCyfr(liczba);
        System.out.println("Suma silni cyfr w liczbie " + liczba + " wynosi " + sumaSilniCyfr);
    }

    public static int obliczSumeSilniCyfr(int liczba) {
        int suma = 0;

        while (liczba != 0) {
            int cyfra = liczba % 10;
            suma += silnia(cyfra);
            liczba /= 10;
        }

        return suma;
    }

    public static int silnia(int n) {
        if (n == 0) {
            return 1;
        } else {
            int wynik = 1;
            for (int i = 1; i <= n; i++) {
                wynik *= i;
            }
            return wynik;
        }
    }
}


Sprawdź, czy liczba jest liczbą pierwszą, czyli ma dokładnie dwa dzielniki: 1 i samą siebie.


import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Wprowadź liczbę: ");
        int liczba = scanner.nextInt();
        scanner.close();

        if (czyLiczbaPierwsza(liczba)) {
            System.out.println(liczba + " jest liczbą pierwszą.");
        } else {
            System.out.println(liczba + " nie jest liczbą pierwszą.");
        }
    }

    public static boolean czyLiczbaPierwsza(int liczba) {
        if (liczba <= 1) {
            return false; // Liczby mniejsze lub równe 1 nie są liczbami pierwszymi
        }

        if (liczba <= 3) {
            return true; // Liczby 2 i 3 są liczbami pierwszymi
        }

        if (liczba % 2 == 0 || liczba % 3 == 0) {
            return false; // Liczby podzielne przez 2 lub 3 nie są liczbami pierwszymi
        }

        // Sprawdzanie dzielników większych od 3
        for (int i = 5; i * i <= liczba; i += 6) {
            if (liczba % i == 0 || liczba % (i + 2) == 0) {
                return false;
            }
        }

        return true; // Jeśli nie znaleziono żadnych dzielników, to liczba jest pierwsza
    }
}




Wygeneruj hasło losowe. Długość hasła powinna wynosić 20 znaków, a ponadto powinno zawierać liczby, wielkie i małe litery oraz znaki specjalne.


import java.security.SecureRandom;

public class Main {
    public static void main(String[] args) {
        String haslo = generujHaslo(20);
        System.out.println("Wygenerowane hasło: " + haslo);
    }

    public static String generujHaslo(int dlugosc) {
        String znakiSpecjalne = "!@#$%^&*()-_=+[]{}|;:,.<>?";
        String liczby = "0123456789";
        String maleLitery = "abcdefghijklmnopqrstuvwxyz";
        String wielkieLitery = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

        String dostepneZnaki = znakiSpecjalne + liczby + maleLitery + wielkieLitery;

        SecureRandom random = new SecureRandom();
        StringBuilder haslo = new StringBuilder();

        for (int i = 0; i < dlugosc; i++) {
            int indeks = random.nextInt(dostepneZnaki.length());
            char znak = dostepneZnaki.charAt(indeks);
            haslo.append(znak);
        }

        return haslo.toString();
    }
}



1.wylosuj 100 liczb z zakrsu od 100 do 150
2.oblicz sume wylosowanych liczb
3.ile roznych liczb wylosowano
4.ktora liczba zostala wylosowana najwiecej razy
5.wypisz liczby palindronowe z wylosowanych

import java.util.ArrayList;
import java.util.HashSet;
import java.util.Random;

public class Main {

    public static ArrayList<Integer> losujLiczby(){
        ArrayList<Integer> wylosowane = new ArrayList<>();
        for (int i = 0; i < 100; i++) {
            wylosowane.add((int)(Math.random()*51+100));
        }
        return wylosowane;
    }
    public static int sumaZListy(ArrayList<Integer> liczbyDoSumowania){
        int suma =0;
        for (Integer liczba: liczbyDoSumowania) {
            suma =suma +liczba;
        }
        return suma;
    }
    public static HashSet<Integer> zapiszDoZbioru(ArrayList<Integer> liczbyDoZapisu){
        HashSet<Integer> zbior = new HashSet<>();
        zbior.addAll(liczbyDoZapisu);
        return zbior;

    }
    public static void ileRazy(ArrayList<Integer> wszystkieLiczby){
        HashSet<Integer> bezpowt = zapiszDoZbioru(wszystkieLiczby);
        ArrayList<Integer>ilePowtorzen = new ArrayList<>();
        for (int i = 0; i < 151; i++) {
            ilePowtorzen.add(0);
        }
        for (Integer liczba:bezpowt
        ) {
            for (Integer liczbapowt: wszystkieLiczby
            ) {
                if(liczba == liczbapowt){
                    ilePowtorzen.set(liczba,ilePowtorzen.get(liczba)+1);
                }
            }
        }
        int maksimum = 0;
        for (int ile:ilePowtorzen) {
            if(maksimum<ile)
                maksimum = ile;
        }
        System.out.println(ilePowtorzen);
        System.out.println(maksimum);
        System.out.println(ilePowtorzen.indexOf(maksimum));
    }
    public static void main(String[] args) {
        ArrayList<Integer> wylosowaneLiczby = losujLiczby();
        System.out.println(wylosowaneLiczby);
        System.out.println(sumaZListy(wylosowaneLiczby));
        HashSet<Integer> liczbyBezPowtorzen = zapiszDoZbioru(wylosowaneLiczby);
        System.out.println("liczb bez powtórzeń "+liczbyBezPowtorzen.size());
        ileRazy(wylosowaneLiczby);
        for (Integer liczba: wylosowaneLiczby
        ) {
            if(liczba % 10 == 1){
                System.out.println(liczba);
            }
        }
    }
}



import java.util.ArrayList;

public class Main {

    public static ArrayList<Integer> fibonaci(){
        ArrayList<Integer> fibo = new ArrayList<>();
        fibo.add(0);
        fibo.add(1);
        int index = 2;
        while(fibo.size()<40){
            fibo.add(fibo.get(index-1)+fibo.get(index-2));
            index++;
        }
        System.out.println(fibo);
        return fibo;
    }
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }

}\\\





@@ -14,8 +14,34 @@ public static ArrayList<Integer> fibonaci(){
        System.out.println(fibo);
        return fibo;
    }
    public static void main(String[] args) {
        System.out.println("Hello world!");

    public static Integer wyszukiwanieBinarne(ArrayList<Integer> listawysz, int szukana) {
        int liczba = 0;
        int poczatek = 0;
        int koniec = listawysz.size() - 1;

        while (koniec - poczatek > 1) {
            int srodek = (poczatek + koniec) / 2;
            if (listawysz.get(srodek) > szukana) {
                koniec = srodek;
            } else {
                poczatek = srodek;
            }
        }
        int roznica1 = szukana - listawysz.get(poczatek);
        int roznica2 = listawysz.get(koniec) - szukana;
        if (roznica1 > roznica2) {
            liczba = listawysz.get(koniec);
        } else {
            liczba = listawysz.get(koniec);
        }
        return liczba;
    }

}
        public static void main (String[]args){
            System.out.println("Hello world!");
            ArrayList<Integer> fibki = fibonaci();
            System.out.println(wyszukiwanieBinarne(fibki, 54));
            System.out.println("test");        }

    }
    
    
    
    
           return liczba;
    }
        public static boolean czyPalidrom(String slowo) {
            return true;
        String slowoOdkonca = "";
            for (int i = 0; i <slowo.length() ; i++) {
                slowoOdkonca = slowo.charAt(i)+slowoOdkonca;
            }
            if(slowo.equals(slowoOdkonca)){
                return true;
            }
            else{
                return false;
            }
        }
        public static void main (String[]args){
            System.out.println("Hello world!");
            ArrayList<Integer> fibki = fibonaci();
            System.out.println(wyszukiwanieBinarne(fibki, 54));
            System.out.println(czyPalidrom("kajak"));
        }

    }
    
    
    
    
                 return false;
            }
        }

        public static Integer liczbaPalindromiczna(Integer liczba){
        Integer pomoc = liczba;
            Integer pomoc2 = liczba;
        while(!czyPalidrom(liczba.toString())){
            liczba++;
        }
        while(!czyPalidrom(pomoc2.toString())){
            pomoc2--;
        }
        return liczba - pomoc > pomoc-pomoc2 ? pomoc2: liczba;
        }

        public static void main (String[]args){
            System.out.println("Hello world!");
            ArrayList<Integer> fibki = fibonaci();
            System.out.println(wyszukiwanieBinarne(fibki, 54));
            System.out.println(czyPalidrom("kajak"));
            System.out.println(liczbaPalindromiczna(790));
        }

    }
