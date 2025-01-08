1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
   SELECT `st`.\*
   FROM `students` AS `st`

    JOIN `degrees` AS `dg`
    ON `st`.`degree_id` = `dg`.`id`

    WHERE `dg`.`name` LIKE "% Economia";

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze
   SELECT `dg`.\*
   FROM `degrees` AS `dg`

    JOIN `departments` AS `dep`
    ON `dg`.`department_id` = `dep`.`id`

    WHERE `dg`.`name` LIKE "% Magistrale %" AND
    `dep`.`name` LIKE "% Neuroscienze";

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
   SELECT `c`.\*
   FROM `teachers` AS `t`

    JOIN `course_teacher` AS `c_t`
    ON `t`.`id` = `c_t`.`teacher_id`

    JOIN `courses` AS `c`
    ON `c`.`id` = `c_t`.`course_id`

    WHERE `t`.`id` = 44;

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome
   SELECT `st`.`id`,
   `st`.`surname`,
   `st`.`name`,
   `st`.`date_of_birth`,
   `st`.`fiscal_code`,
   `st`.`enrolment_date`,
   `st`.`registration_number`,
   `st`.`email`,

    `d`.`id` AS `department_id`,
    `d`.`name` AS `department_name`,
    `d`.`level` AS `department_level`,
    `d`.`address` AS `department_address`,
    `d`.`email` AS `department_email`,
    `d`.`website` AS `department_website`,

    `c`.`id` AS `course_id`,
    `c`.`name` AS `course_name`,
    `c`.`description` AS `course_description`,
    `c`.`period` AS `course_period`,
    `c`.`year` AS `course_year`,
    `c`.`cfu` AS `course_cfu`,
    `c`.`website` AS `course_website`
    FROM `students` AS `st`

    JOIN `degrees` AS `d`
    ON `st`.`degree_id` = `d`.`id`

    JOIN `courses` AS `c`
    ON `d`.`id` = `c`.`degree_id`

    ORDER BY `st`.`surname`,`st`.`name` ASC;

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
   SELECT `d`.`id` AS `degrees_id`,
   `d`.`name` AS `degrees_name`,
   `d`.`level` AS `degrees_level`,
   `d`.`address` AS `degrees_address`,
   `d`.`email` AS `degrees_email`,
   `d`.`website` AS `degrees_website`,

    `c`.`id` AS `course_id`,
    `c`.`name` AS `course_name`,
    `c`.`description` AS `course_description`,
    `c`.`period` AS `course_period`,
    `c`.`year` AS `course_year`,
    `c`.`cfu` AS `course_cfu`,
    `c`.`website` AS `course_website`,

    `t`.`id` AS `teacher_id`,
    `t`.`name` AS `teacher_name`,
    `t`.`surname` AS `teacher_surname`,
    `t`.`phone` AS `teacher_phone`,
    `t`.`email` AS `teacher_email`,
    `t`.`office_address` AS `teacher_office_address`,
    `t`.`office_number` AS `teacher_office_number`
    FROM `degrees` AS `d`

    JOIN `courses` AS `c`
    ON `d`.`id` = `c`.`degree_id`

    JOIN `course_teacher` AS `c_t`
    ON `c`.`id` = `c_t`.`course_id`

    JOIN `teachers` AS `t`
    ON `c_t`.`teacher_id` = `t`.`id`

    ORDER BY `d`.`name` ASC;

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)
   SELECT DISTINCT `t`.`id` AS `teacher_id`,
   `t`.`surname` AS `teacher_surname`,
   `t`.`name` AS `teacher_name`,
   `t`.`phone` AS `teacher_phone`,
   `t`.`email` AS `teacher_email`,
   `t`.`office_address` AS `teacher_office_address`,
   `t`.`office_number` AS `teacher_office_number`
   FROM `departments` AS `dep`

    JOIN `degrees` AS `d`
    ON `dep`.`id` = `d`.`department_id`

    JOIN `courses` AS `c`
    ON `d`.`id` = `c`.`degree_id`

    JOIN `course_teacher` AS `c_t`
    ON `c`.`id` = `c_t`.`course_id`

    JOIN `teachers` AS `t`
    ON `c_t`.`teacher_id` = `t`.`id`

    WHERE `dep`.`id` = 5

    ORDER BY `t`.`surname`, `t`.`name` ASC;

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.
   SELECT `st`.`id`,
   `st`.`surname`,
   `st`.`name`,
   `c`.`name` AS `course_name`,
   COUNT(`e`.`id`) AS `student_attempts`,
   MAX(`e_st`.`vote`) AS `max_vote`

    FROM `students` AS `st`

    JOIN `exam_student` AS `e_st`
    ON `st`.`id` = `e_st`.`student_id`

    JOIN `exams` AS `e`
    ON `e_st`.`exam_id` = `e`.`id`

    JOIN `courses` AS `c`
    ON `e`.`course_id` = `c`.`id`

    WHERE `e_st`.`vote` >= 18

    GROUP BY `st`.`id`, `c`.`id`

    ORDER BY `st`.`surname`, `st`.`name`, `course_name` ASC;
