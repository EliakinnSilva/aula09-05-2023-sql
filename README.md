# aula09-05-2023-sql

--USE teste;

CREATE FUNCTION F_Situacao(@Nota1 FLOAT, @Nota2 FLOAT, @Nota3 FLOAT)
       RETURNS VARCHAR(11)
AS
       BEGIN
	        DECLARE @media FLOAT = (@Nota1+@Nota2+@Nota3)/3;
			RETURN(IIF(@media<5,'Reprovado', IIF(@media<7, 'Recuperacao', 'Aprovado')));
	   END;

--CREATE DATABASE ALUNO;
--USE ALUNO;

--CREATE TABLE Aluno (
--   Nome VARCHAR(50) NOT NULL,
--   Nota1 FLOAT NOT NULL,
--   Nota2 FLOAT NOT NULL,
--   Nota3 FLOAT NOT NULL
--);

--INSERT INTO Aluno (Nome, Nota1, Nota2, Nota3)
--VALUES ('PEDRO',2,7,4),
--       ('CARLOS',4,9,6),
--       ('ANA',6,1,8),
--       ('PAULO',8,3,10),
--       ('MARIA',10,5,9),
--       ('JOÃO',3,9,7),
--       ('CRISTINA',5,2,6),
--       ('JOSÉ',1,7,8);

--SELECT * FROM Aluno;

Select Nome As 'NOME',
		Nota1 AS'NOTA1',
		Nota2 AS 'NOTA2',
		Nota3 AS 'NOTA3',
		CAST ((Nota1+Nota2+Nota3)/3 AS Decimal(3,1)) as 'Média',
		dbo.F_Situacao(Nota1,Nota2,Nota3) as 'SITUAÇÃO'
FROM Aluno

SELECT * FROM sysobjects
