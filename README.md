# login mysql, password is in .env (root)
docker exec -it <your> mysql -u root -p
e.g: docker exec -it pest_db_v1 mysql -u root -p
# change database
e.g: USE pest_db_v1;
# show tables in your database
e.g: SHOW TABLES;
# show the latest 5 data 
e.g: SELECT * FROM pest_records ORDER BY id DESC LIMIT 5;
e.g: SELECT * FROM user_profiles ORDER BY id DESC LIMIT 5;