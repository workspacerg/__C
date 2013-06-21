__C SQL
===

Projet Ecole CheckSQL

-----------------------------------------------------------------------------------------------------------------


Exportation du schéma et des données

Votre MiniSQL devra permettre d'exporter les schémas de table ainsi que les données en langage

SQL pour être facilement importable à partir d'un SGBD tel que MySQL.

L'exportation devra être possible à partir d'une pseudo commande SQL :

EXPORT SCHEMA(<tablename>,<tablename>...) INTO <filename>

EXPORT SCHEMA(*) INTO <filename>

EXPORT DATAS(<tablename>,<tablename>...) INTO <filename>

EXPORT DATAS(*) INTO <filename>

-----------------------------------------------------------------------------------------------------------------


Implémentation du langage SQL

Voici un exemple de scénario SQL que votre miniSQL devra prendre en charge.

CREATE TABLE user (user_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, login VARCHAR(50),

password VARCHAR(50), active INT, connections INT, last_connection DATE) 

CREATE TABLE role (role_id INT NOT NULL PRIMARY KEY AUTO_INCREMENT, name VARCHAR(50),

decription varchar(255)) ;

CREATE TABLE user_role (user_id INT, role_id INT) ; 

INSERT INTO user (user_id, login, password, active, connections, last_connection) 

VALUES (1, 'julien', 'mdp', 0, 0, 0) ;

INSERT INTO role (role_id, name) VALUES (1, 'admin') ;

INSERT INTO user_role(user_id, role_id) VALUES(1,1) ;

UPDATE user SET active=1 WHERE login='julien' ;

SELECT user.* 

FROM user, role, role_user 

WHERE role.name='admin' AND role_user.role_id = role.role_id AND role_user.user_id = user.user_id ORDER BY

name DESC LIMIT 10 OFFSET 0

DELETE FROM user WHERE login='julien'

Concernant la clause WHERE le opérateurs relationnels et logique devront être complètement

implémentés pour tous les types de données.

Concernant la clause ORDER BY, l'ordre devra pouvoir être ASCendant ou DESCendant

