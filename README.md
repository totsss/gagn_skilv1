# gagn_skilv1

use 1608003640_saleco;

create table customer(
	CUS_code varchar(255) primary key,
    CUS_LNAME varchar(55),
    Cus_inital varchar(2),
    CUS_areacode varchar (255),
    CUS_phone varchar(11),
    CUS_balance int(20)
    );
    
create table invoice(
	inv_nuber int (11) Primary key,
    CUS_code varchar (255),
    inv_date varchar(20)
    );

Create table line (
	lin_number int (100) primary key,
    line_units varchar (255),
    line_price varchar (50),
    inv_number int(11),
    prod_code varchar(50)
    );
    
create table product (
	prod_code varchar (255) primary key,
    prod_descript varchar (255),
    prod_price varchar (25),
    prod_on_hand varchar (255),
    inv_number int(11)
    );

create table verdor (
	vend_code varchar (255),
    vend_contact varchar(255),
    vend_areacode varchar (255) primary key,
    vend_phone varchar(11),
    cus_code varchar (255)
	);

insert into customer values
('10010','Ramas','Alfred','A','0181','844-2573',0),
('10011','Dunne','Leona','K','0161','894-1238',0),
('10012','Smith','Kathy','W','0181','894-2285',345.86);

insert into invoice values
(1001,10010,'2008-01-16'),
(1002,10011,'2008-01-16'),
(1003,10012,'2008-01-16')
;

insert into product values
('11QER/31','Power painter','109.99','122',1001),
('13-Q2/P2','7.25-cm. pwr. saw blade','14.99','123',1002),
('14-Q1/L3','9.00-cm. pwr. saw blade','17.49','111',1003);
;

insert into verdor values 
(21225,'Bryson, Inc.','Smithson','223-3234',10010),
(21226,'SuperLoo, Inc.','Flushing','215-8995',10011),
(21231,'D\&E Supply','Singh','228-3245',10012);

insert into line values
(1,'1','14.99',1001,'11QER/31'),
(2,'3','9.95',1002,'13-Q2/P2'),
(4,'2','4.99',1003,'14-Q1/L3');

alter table customer ADD CONSTRAINT
PRIMARY KEY (CUS_CODE);

ALTER table invoice ADD constraint FOREIGN KEY (CUS_CODE)
REFERENCES customer (CUS_CODE);

alter table line ADD CONSTRAINT
PRIMARY KEY (LIN_NUMBER);


ALTER TABLE INVOICE ADD constraint primary key (INV_NUMBER);

ALTER TABLE product ADD constraint primary key (PROD_CODE);

ALTER TABLE line ADD INV_NUMBER INT not null,
ADD PROD_CODE VARCHAR (50) not null;

ALTER TABLE customer ADD VEND_AREACODE INT not null;

ALTER TABLE VERDOR ADD constraint primary key (VEND_AREACODE);


ALTER table customer ADD constraint FOREIGN KEY (VEND_AREACODE)
REFERENCES verdor (VEND_AREACODE);

ALTER table line ADD constraint FOREIGN KEY (INV_NUMBER)
REFERENCES invoice (INV_NUMBER);

ALTER table line ADD constraint FOREIGN KEY (PROD_CODE)
REFERENCES product (PROD_CODE);

ALTER TABLE verdor ADD CUS_CODE varchar (255) not null;

ALTER table verdor ADD constraint FOREIGN KEY (CUS_CODE)
REFERENCES customer (CUS_CODE);

alter table verdor drop CUS_CODE;

ALTER TABLE product ADD LINE_NUMBER INT (100) not null;

 
 ALTER TABLE line
ADD constraint foreign key (inv_number) references invoice (inv_number);
 
ALTER TABLE invoice
ADD FOREIGN KEY ('inv_number') REFERENCES invoice('inv_number');


alter table line
add constraint foreign key(prod_code) references product(prod_code);






