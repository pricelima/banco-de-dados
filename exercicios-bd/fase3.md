## 1) ordenando alunos por nascimento:
SELECT nome, data_nascimento FROM alunos ORDER BY data_nascimento;

## 2) consulta que mostre os alunos que nasceram antes do ano 2009
SELECT * FROM alunos WHERE data_nascimento < '2009-01-01';

## 3) consulta que calcula a média das notas de cada aluno e as mostra com duas casas decimais.
SELECT nome, ROUND(AVG((primeira_nota + segunda_nota)/2), 2) AS media FROM alunos GROUP BY id;

## 3) consulta que calcule o limite de faltas de cada curso de acordo com a carga horária. Considerando o limite como 25% da carga horária. Classificando em ordem crescente pelo título do curso.
SELECT titulo, carga_horaria, ROUND(carga_horaria * 0.25) AS 'limite' FROM cursos ORDER BY titulo;


## 4) consulta que mostra os nomes somente dos professores da área de desenvolvimento.
SELECT nome FROM professores WHERE area_atuacao = 'desenvolvimento';
SELECT * FROM professores WHERE area_atuacao = 'desenvolvimento';

## 5) consulta que mostra a quantidade de professores por área de desenvolvimento. 
SELECT COUNT(id) AS 'quantidade' FROM professores WHERE area_atuacao = 'desenvolvimento';


## 6) consulta que mostra o nome dos alunos, o título e a carga horária dos cursos que fazem.  ERRO
SELECT alunos.nome, cursos.titulo, cursos.carga_horaria FROM alunos LEFT JOIN cursos ON alunos.id_curso = cursos.id ORDER BY alunos.nome;


## 7) consulta que mostra o nome dos professores e o título do curso que lecionam. Classificando pelo nome do professor.
SELECT professores.nome, cursos.titulo FROM professores LEFT JOIN cursos ON professores.id_curso = cursos.id ORDER BY professores.nome;

## 8)consulta que mostra o nome dos alunos, o título dos cursos que fazem, e o professor de cada curso.
SELECT alunos.nome, cursos.titulo, professores.nome FROM alunos LEFT JOIN cursos ON alunos.id_curso = cursos.id LEFT JOIN professores ON professores.id_curso = cursos.id;

## 9)consulta que mostre a quantidade de alunos que cada curso possui. Resultados em ordem descrecente de acordo com a quantidade de alunos.
SELECT cursos.titulo AS `curso`, COUNT(alunos.id_curso) AS `quantidade` FROM alunos LEFT JOIN CURSOS ON alunos.id_curso = cursos.id GROUP BY curso ORDER BY `quantidade` DESC;

## 10) Faça uma consulta que mostre o nome dos alunos, suas notas, médias, e o título dos cursos que fazem. Devem ser considerados somente os alunos de Front-End e Back-End. Mostre classificados pelo nome do aluno.
SELECT alunos.nome, alunos.primeira_nota, alunos.segunda_nota, ROUND(((alunos.primeira_nota + alunos.segunda_nota)/2), 2) AS `media`, professores.nome FROM alunos LEFT JOIN cursos ON alunos.id_curso = cursos.id LEFT JOIN professores ON professores.id_curso = cursos.id WHERE cursos.id = 1 OR cursos.id = 2;

## 11) Consulta que altera o nome do curso Figma para Adobe XD e a carga horária de 10 para 15.
UPDATE cursos SET titulo = 'Adobe XD', carga_horaria = 15 WHERE id = 4;

## 12)Consulta que exclua um aluno do curso de Redes de Computadores e um aluno do curso de UX/UI.
--confirmar os alunos com select: 
SELECT  nome, id, id_curso FROM alunos WHERE id_curso = 6 OR id_curso = 8 ;
SELECT nome FROM alunos WHERE id = 11 OR id = 13;

--deletar os alunos encontrados:
DELETE FROM alunos WHERE id = 11 OR id = 13;

## 13) Consulta que mostra a lista de alunos atualizada e o título dos cursos que fazem, classificados pelo nome do aluno.
SELECT alunos.nome AS `Alunos`, cursos.titulo AS `Cursos` FROM alunos LEFT JOIN CURSOS ON alunos.id_curso = cursos.id group by alunos;

## Encontrando a idade dos alunos:
SELECT nome AS `Aluno`, TIMESTAMPDIFF(YEAR, data_nascimento, CURDATE()) AS `Idade` FROM alunos;

## Encontrando a média
SELECT nome, ROUND(((primeira_nota + segunda_nota)/2), 2) AS `Média` FROM alunos;

## Encontrando a média das notas de cada aluno mostrando alunos que tiveram a média maior ou igual a 7.
SELECT nome, ROUND(((primeira_nota + segunda_nota)/2), 2) AS `media` FROM alunos WHERE ROUND(((primeira_nota + segunda_nota)/2), 2) >= 7.0 ;

## Encontrando a média das notas de cada aluno mostrando alunos que tiveram a média menor que 7.
SELECT nome, ROUND(((primeira_nota + segunda_nota)/2), 2) AS `media` FROM alunos WHERE ROUND(((primeira_nota + segunda_nota)/2), 2) < 7.0 ;

## Encontrando a quantidade de alunos com média maior ou igual a 7.
SELECT COUNT(id) FROM alunos WHERE ROUND(((primeira_nota + segunda_nota)/2), 2) >= 7.0;





