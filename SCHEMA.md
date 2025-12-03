## DB UNIVERSITY 

# Traccia

Modellizzare la struttura di un database per memorizzare tutti i dati riguardanti una università:

sono presenti diversi Dipartimenti (es.: Lettere e Filosofia, Matematica, Ingegneria ecc.);

ogni Dipartimento offre più Corsi di Laurea (es.: Civiltà e Letterature Classiche, Informatica, Ingegneria Elettronica ecc..)

ogni Corso di Laurea prevede diversi Corsi (es.: Letteratura Latina, Sistemi Operativi 1, Analisi Matematica 2 ecc.);

ogni Corso può essere tenuto da diversi Insegnanti;

ogni Corso prevede più appelli d'Esame;

ogni Studente è iscritto ad un solo Corso di Laurea;

ogni Studente può iscriversi a più appelli di Esame;

per ogni appello d'Esame a cui lo Studente ha partecipato, è necessario memorizzare il voto ottenuto, anche se non sufficiente.

Pensiamo a quali entità (tabelle) creare per il nostro database e cerchiamo poi di stabilirne le relazioni.

Infine, andiamo a definire le colonne e i tipi di dato di ogni tabella.

## Entity

departments
degree_courses
courses
teachers
student
exam_session
pivot (exam-session student many)
pivot(courses teacher many)

## Table_name: departments (entity_name:department)

id: AUTO_INCREMENT PK BIGINT UNSIGNED
name: VARCHAR (80)

## Table_name: degree_courses (entity_name:degree_course)

id: AUTO_INCREMENT PK BIGINT UNSIGNED
department_id: BIGINT UNSIGNED FK
name: VARCHAR(80)

## Table_name: courses (entity_name:course)

id: AUTO_INCREMENT PK BIGINT UNSIGNED
identify_code:
name: VARCHAR(80)
year: CHAR(7)  example(2025-26)

## Table_name: teachers (entity_name:teacher)

id: AUTO_INCREMENT PK BIGINT UNSIGNED
name: VARCHAR(30)
last_name: VARCHAR(30)
identify_code: CHAR(6)
email: VARCHAR(40)
phone: VARCHAR(13)

## Table_name: students (entity_name:student)

id: AUTO_INCREMENT PK BIGINT UNSIGNED
name: VARCHAR(30)
last_name: VARCHAR(30)
identify_code: CHAR(6)
email: VARCHAR(40)
phone: VARCHAR(13)

## Table_name: exam_sessions (entity_name:exam_session)

id: AUTO_INCREMENT PK BIGINT UNSIGNED
exam_date: DATETIME(Date.now())
room: VARCHAR (20)

## Pivot-table:exam_session_students

exam_session_id: FK BIGINT UNSIGNED
student_id: FK BIGINT UNSIGNED
vote: TINYINT 

## Pivot-table:courses many_teachers

courses_id: FK BIGINT UNSIGNED
teachers_id: FK BIGINT UNSIGNED 