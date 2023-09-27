# SQL_Data_Cleaning
Varsity DataBase

select avg(weight_in_lbs) as average_weight_in_lbs from entries;

select *, COALESCE(weight_in_lbs, 90.45) as corrected_weights from entries;

select avg(corrected_weights) from
(select *, COALESCE(weight_in_lbs, 90.45) as corrected_weights from entries) as subquery;

select id, name, dept_name from
student_metadata s join department_details d
on s.dept_id = d.dept_id;

select id, name, dept_name from
student_metadata s join department_details d
on s.dept_id = cast(d.dept_id as smallint);

select dept_name, count(dept_name) as student_count
from student_details
group by dept_name;

select upper(replace(dept_name, 'Information Technology', 'I.T')) as dept_cleaned,
count(dept_name) as student_count
from student_details
group by dept_cleaned;

select upper(replace(dept_name, 'Information Technology', 'I.T')) as dept_cleaned,
count(dept_name) as student_count
from student_details
group by dept_cleaned;

select date_part('month', birthdate) from employees;

select date_part('month', CAST(birthdate AS date)) as birthday_months from employees;

select band_name, sum(total_show_count) as total_shows, sum(performed) as total_times_performed
from band_details b join some_festival_record s
on b.id = s.band_id
group by band_name;

select band_name, total_show_count, sum(performed) as total_times_performed
from band_details b join some_festival_record s
on b.id = s.band_id
group by band_name, total_show_count;

