create table Regions (

region_id int not null primary key,
name varchar(25) not null

)

insert into Regions ( region_id, name)
values (1, 'Europe')

insert into Regions ( region_id, name)
values (2, 'North America')

insert into Regions ( region_id, name)
values (3, 'Asia')

insert into Regions ( region_id, name)
values (4, 'Australia')

create table Countries  (

country_id char(2) not null primary key,
name varchar(25) not null,
region_id int not null
)

alter table Countries 

add constraint fk_countries_regions foreign key(region_id)
references Regions(region_id)

insert into Countries (country_id, name, region_id) 
values ('BG', 'Bulgaria', 1) 

insert into Countries (country_id, name, region_id) 
values ('CA', 'Canada', 2) 

insert into Countries (country_id, name, region_id) 
values ('CH', 'China', 3) 

insert into Countries (country_id, name, region_id) 
values ('AU', 'Australia', 4) 


create table Customers (

company_name varchar(25) not null,
customer_id int not null primary key,
country_id char(2) not null, 
first_name varchar(20) not null,
last_name varchar(20) not null,
address text null,
email  varchar(25) not null,
)

alter table Customers 

add constraint fk_customer_country foreign key(country_id)
references Countries (country_id)


insert into Customers ( company_name, customer_id, country_id, first_name, last_name, email)
values ( 'Venk limited', 1, 'BG', 'Ventsislav', 'Kostadinov',  'norter@abv.bg')

insert into Customers ( company_name, customer_id, country_id, first_name, last_name, email)
values ( 'Venk Solutions', 2, 'CA', 'Ivan', 'Ivanov',  'ivanvv@abv.bg')

insert into Customers ( company_name, customer_id, country_id, first_name, last_name, email)
values ( 'Chon Park limited', 3, 'CH', 'Chon', 'park',  'chonp@abv.bg')

insert into Customers ( company_name, customer_id, country_id, first_name, last_name, email)
values ( 'Brian PC trade', 4, 'AU', 'Brian', 'Thomasson',  'brian@abv.bg')


create table Products (

product_id int not null primary key, 
name   varchar(20) not null,
price  numeric(6,2) not null,
)

insert into Products 
values (1101, 'Inter Core-i3', 280.45)

insert into Products 
values (1102, 'Intel Core-i5', 480.20)

insert into Products 
values (1103, 'Inter Core-i7', 580.80)

create table Employees (

employee_id int not null primary key,
first_name varchar(20) not null,
last_name varchar(20) not null,
email varchar(20) not null,
phone varchar(15) not null,
)

insert into Employees 
values ( 1234, 'Nikolay', 'Rumenov', 'rumenov@abv.bg', '+359897455885')

insert into Employees 
values ( 1235, 'Ventsislav', 'Kostadinov', 'venk@abv.bg', '+359897455886')

create table Orders (

order_id int not null primary key,
order_date datetime not null,
product_id int not null,
customer_id int not null,
customer_first_name varchar(25) not null,
customer_last_name varchar(25) not null,
phone varchar(15) not null,

)

alter table Orders 

add constraint fk_customer_employee foreign key(customer_id)
references Employees(employee_id)

alter table Orders

add constraint fk_customer_customer foreign key(customer_id)
references Customers(customer_id)

alter table Orders 

add constraint fk_order_product foreign key(product_id)
references Products(product_id)

alter table Orders
drop constraint fk_customer_customer

insert into Orders 
values ( 168947, '11/07/2016', 1101, 1234, 'Georgi', 'Georgiev', '+359889987882')