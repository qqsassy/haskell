-- Twoim zadaniem jest stworzenie funkcji w Haskelu o nazwie sumList, 
-- która obliczy sumę wszystkich elementów w liście liczb całkowitych. 
-- Zamiast liczyć ręcznie skorzystaj z eleganckiej metody rekurencji.
sumList :: [Int] -> Int
sumList []     = 0
sumList (x:xs) = x + sumList xs

main :: IO ()
    main = print (sumList [1, 2, 3, 4, 5])


-- Masz za zadanie stworzyć funkcję w haskelu, która wygeneruje wszystkie możliwe, 
-- unikalne dwuelementowe krotki z zestawu {ogien, woda, powietrze, ziemia} eliminując powtórzenia.
perm :: [String] -> [(String, String)]
perm [] = []
perm (first:rest) = [(first, x) | x <- rest] ++ perm rest

zywioly :: [String]
zywioly = ["ogien", "ziemia", "powietrze", "woda"]

main :: IO ()
main = do
    let pary = perm zywioly
    print pary


-- Masz za zadanie napisać program w prologu, który będzie rozwiązywał problem kolorowania grafu, 
-- w którym wierzchołki reprezentują wioski, a krawędzie łączące te wioski oznaczają, że wioski sąsiadują ze sobą. 
-- Graf jest reprezentowany przez zestaw połączeń, a twoje zadanie polega na tym, 
-- przypisać do każdego wierzchołka jeden z trzech kolorów (zielony, czerwony, niebieski), 
-- przy czym sąsiednie węzły nie mogą mieć tego samego koloru
% Kolory
color(red).
color(green).
color(blue).

% Dozwolone kombinacje kolorów dla sąsiadujących wierzchołków
neighbor(green, red).
neighbor(green, blue).
neighbor(red, green).
neighbor(red, blue).
neighbor(blue, green).
neighbor(blue, red).

% Sąsiedztwa między wioskami
edge(a, b).
edge(a, c).
edge(b, c).
edge(b, d).
edge(c, d).
edge(d, e).

% Główna reguła kolorowania
coloring(A, B, C, D, E) :-
    color(A),
    color(B),
    color(C),
    color(D),
    color(E),

    % Wierzchołki sąsiadujące muszą mieć różne kolory wg predykatu neighbor/2
    neighbor(A, B),
    neighbor(A, C),
    neighbor(B, C),
    neighbor(B, D),
    neighbor(C, D),
    neighbor(D, E).
