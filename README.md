# PostgreSQL-b-sico-Alunos-e-Disciplinas-

--Cria a tabela Alunos

CREATE TABLE Alunos(
	id_aluno INT PRIMARY KEY,
	nome VARCHAR(100),
	idade INT,
	curso VARCHAR(100)
);

--Cria a tabela Disciplinas

CREATE TABLE Disciplinas(
	id_disciplina INT PRIMARY KEY,
	nome_disciplina VARCHAR(100),
	id_aluno_disc INT,
	FOREIGN KEY (id_aluno_disc) REFERENCES Alunos (id_aluno)
);

--Insere valores na tabela Alunos

INSERT INTO Alunos VALUES (1, 'João', 22, 'Sistemas de Informação');
INSERT INTO Alunos VALUES (2, 'Maria', 21, 'Análise e Desenvolvimento de Sistemas');
INSERT INTO Alunos VALUES (3, 'Pedro', 23, 'Engenharia de Software');
INSERT INTO Alunos VALUES (4, 'Angela', 25, 'Análise e Desenvolvimento de Sistemas');

--Insere valores na tabela Disciplinas

INSERT INTO Disciplinas VALUES (1, 'Redes de Computadores', 1);
INSERT INTO Disciplinas VALUES (2, 'Programação 1', 2);

--Consulta todos os alunos com mais de 21 anos

SELECT nome, idade
FROM Alunos
WHERE idade > 21;

--Atualiza a idade no aluno João para 23

UPDATE Alunos
SET idade = 23
WHERE id_aluno = 1;

--Seleciona a tabela Alunos

SELECT * FROM Alunos;

--Exclui a tupla onde tem o nome de Pedro

DELETE FROM Alunos
WHERE nome = 'Pedro';

/*Junção de tabelas onde mostra o nome do aluno 
e o nome da disciplina que ele está cursando*/

SELECT nome, nome_disciplina
FROM Alunos
JOIN Disciplinas ON id_aluno = id_aluno_disc;

--Retorna o número total de alunos em cada curso

SELECT COUNT(nome)
FROM Alunos;

/*Seleciona todos os alunos do curso de 
Análise e Desenvolvimento de Sistemas e ordena-os
pela idade em ordem decrescente*/

SELECT curso, idade 
FROM Alunos
WHERE curso = 'Análise e Desenvolvimento de Sistemas'
ORDER BY idade DESC;

/*Seleciona o nome dos alunos cuja idade é maior
que a idade média dos alunos*/
SELECT nome, idade
FROM Alunos
WHERE idade > (SELECT AVG(idade) FROM Alunos);
