# Fase 1
### Criando a base de dados:
CREATE DATABASE tecinternet_escola_veronica CHARACTER SET utf8mb4;
Criando a entidade cursos:

CREATE TABLE cursos(
    id SMALLINT  NOT NULL PRIMARY KEY AUTO_INCREMENT,
    titulo VARCHAR(45) NOT NULL,
    carga SMALLINT NOT NULL,
    professor_id INT NULL
);

### Chave estrangeira:
ALTER TABLE cursos ADD CONSTRAINT fk_professor FOREIGN KEY (professor_id) REFERENCES professores(id);
Criando a entidade professores:

CREATE TABLE professores(
    id SMALLINT  NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(30) NOT NULL,
    area ENUM('desing', 'desenvolvimento', 'infra') NOT NULL,
    curso_id INT NULL
);


### Chave estrangeira:
ALTER TABLE professores ADD CONSTRAINT fk_curso FOREIGN KEY (curso_id) REFERENCES cursos(id);
criando a entidade alunos:

CREATE TABLE alunos(
    id SMALLINT  NOT NULL PRIMARY KEY AUTO_INCREMENT,
    nome VARCHAR(50) NOT NULL,
    nscimento DATE NOT NULL,
    nota1 DECIMAL(4,2) NOT NULL,
    nota2 DECIMAL(4,2) NOT NULL,
    curso_id SMALLINT NOT NULL
);

### Chave estrangeira:
ALTER TABLE alunos ADD CONSTRAINT fk_curso FOREIGN KEY (curso_id) REFERENCES cursos(id);