```SQL
CREATE DATABASE mundo;

CREATE TABLE Pais (
    Nome_pais VARCHAR(35) PRIMARY KEY,
    Continente VARCHAR(35),
    Pop_pais REAL,
    PIB REAL,
    Expec_vida REAL
);

CREATE TABLE Cidade (
    Nome_cidade VARCHAR(35) PRIMARY KEY,
    Pais_origem VARCHAR(35) REFERENCES Pais(Nome_pais),
    Pop_cidade REAL,
    Capital CHAR(1)
);

CREATE TABLE Rio (
    Nome_rio VARCHAR(35) PRIMARY KEY,
    Nascente VARCHAR(35) REFERENCES Pais(Nome_pais),
    Pais_pertencente VARCHAR(35) REFERENCES Pais(Nome_pais),
    Comprimento DECIMAL(4, 1)
);

INSERT INTO Pais (Nome_pais, Continente, Pop_pais, PIB, Expec_vida) VALUES
('Canada', 'Am. Norte', 30.1, 658, 77.08),
('Mexico', 'Am. Norte', 107.5, 694, 69.1),
('Brasil', 'Am. Sul', 183.3, 10004, 65.2),
('USA', 'Am. Norte', 270.0, 8003, 75.5);

INSERT INTO Cidade (Nome_cidade, Pais_origem, Pop_cidade, Capital) VALUES
('Washington', 'USA', 3.3, 'S'),
('Monterrey', 'Mexico', 2.0, 'N'),
('Brasilia', 'Brasil', 1.5, 'S'),
('São Paulo', 'Brasil', 15.0, 'N'),
('Ottawa', 'Canada', 0.8, 'S'),
('Cid. Mexico', 'Mexico', 14.1, 'S');

INSERT INTO Rio (Nome_rio, Nascente, Pais_pertencente, Comprimento) VALUES
('St. Lawrence', 'USA', 'USA', 3.3),
('Grande', 'USA', 'Mexico', 2.0),
('Parana', 'Brasil', 'Brasil', 1.5),
('Mississipi', 'USA', 'USA', 15.0);

-- 1. Liste todas as cidades e os países aos quais pertencem.

SELECT Nome_cidade, Pais_origem
FROM Cidade;

-- 2. Liste todas as cidades que são capitais.

SELECT Nome_cidade
FROM Cidade
WHERE Capital = 'S';

-- 3. Liste todos os atributos dos países onde a expectativa de vida é menor que 70 anos.

SELECT *
FROM Pais
WHERE Expec_vida < 70;

-- 4. Liste todas as capitais e as populações dos países cujos PIB é maior que 1 trilhão de dólares.

SELECT C.Nome_cidade, C.Pop_cidade
FROM Cidade C
JOIN Pais P ON C.Pais_origem = P.Nome_pais
WHERE P.PIB > 1000;  

-- 5. Qual é o nome e a população da capital do país onde o rio St. Lawrence tem sua nascente.

SELECT C.Nome_cidade, C.Pop_cidade
FROM Cidade C
JOIN Rio R ON R.Nascente = C.Pais_origem
WHERE R.Nome_rio = 'St. Lawrence';

-- 6. Qual é a média da população das cidades que não são capitais.

SELECT AVG(Pop_cidade) AS Media_Populacao
FROM Cidade
WHERE Capital = 'N';

-- 7. Para cada continente, retorne o PIB médio de seus países.

SELECT Continente, AVG(PIB) AS PIB_Medio
FROM Pais
GROUP BY Continente;

-- 8. Para cada país onde pelo menos 2 rios têm nascente, encontre o comprimento do menor rio.

SELECT R.nascente, MIN(R.Comprimento) AS Menor_Comprimento
FROM Rio R
GROUP BY R.nascente
HAVING COUNT(R.Nome_rio) >= 2;

-- 9. Liste os países cujo PIB é maior que o PIB do Canadá.

SELECT Nome_pais
FROM Pais
WHERE PIB > (SELECT PIB FROM Pais WHERE Nome_pais = 'Canada');

```