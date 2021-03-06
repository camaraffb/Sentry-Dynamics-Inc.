# Sentry-Dynamics-Inc.

/*------------------------------------------------------------------------------------------------------

PROGRAMMER:   Bakary Camara

LANGUAGE:     mySql

PLATFORM:     OMEGA

CONCEPTS:     The goal for this is to create relational database tables and populate them with data. The 
              tables are then access and manipulated using sql commands.

----------------------------------------------------------------------------------------------------------*/


--Bakary 

--DROP TABLES
DROP TABLE TRANS_DETAIL_bxc;
DROP TABLE TRANSACTION_bxc;
DROP TABLE MEMBER_bxc;
DROP TABLE FEE_bxc;
DROP TABLE COPY_bxc;
DROP TABLE TITLE_bxc;
DROP TABLE CATEGORY_bxc;
DROP TABLE RATING_bxc;

--Part I
--CREATE TABLE STATEMENTS

CREATE TABLE RATING_bxc(
Rating 		VARCHAR(6)	NOT NULL,
RatingDesc	VARCHAR(30)	NOT NULL,
PRIMARY KEY	(Rating));

CREATE TABLE CATEGORY_bxc(
CatID		CHAR(3)		NOT NULL,
CatName		VARCHAR(10)	NOT NULL,
PRIMARY KEY	(CatID));

CREATE TABLE TITLE_bxc(
TitleID 	Number(5)	NOT NULL,
Title		VARCHAR(30)	NOT NULL,
Rating 		VARCHAR(6)	NOT NULL,
CatID		CHAR(3)		NOT NULL,
PRIMARY KEY 	(TitleID),
FOREIGN KEY 	(CatID)		REFERENCES CATEGORY_bxc,
FOREIGN KEY 	(Rating)	REFERENCES RATING_bxc);

CREATE TABLE COPY_bxc(
CopyID		Number(5)	NOT NULL,
TitleID		Number(5)	NOT NULL,
Format		VARCHAR(10)	NOT NULL,
PRIMARY KEY 	(CopyID),
FOREIGN KEY 	(TitleID)	REFERENCES TITLE_bxc);

CREATE TABLE FEE_bxc(
FeeCode		CHAR(2)		NOT NULL,
FeeAmt		Number(4, 2)	NOT NULL,
PRIMARY KEY 	(FeeCode));

CREATE TABLE MEMBER_bxc(
MemberID	Number(5)	NOT NULL,
MemberFName	VARCHAR(20)	NOT NULL,
MemberLName 	VARCHAR(20) 	NOT NULL,
MemberPhone 	CHAR(10),
PRIMARY KEY 	(MemberID));

CREATE TABLE TRANSACTION_bxc(
TransID		Number(6)	NOT NULL,
TransDate	DATE		NOT NULL,
MemberID	Number(5)	NOT NULL,
PRIMARY KEY	(TransID),
FOREIGN KEY 	(MemberID)	REFERENCES MEMBER_bxc);

CREATE TABLE TRANS_DETAIL_bxc(
TransID		Number(6)	NOT NULL,
CopyID		Number(5)	NOT NULL,
FeeCode		CHAR(2)		NOT NULL,
PRIMARY KEY 	(TransID, CopyID),
FOREIGN KEY 	(TransID)	REFERENCES TRANSACTION_bxc,
FOREIGN KEY 	(CopyID) 	REFERENCES COPY_bxc,
FOREIGN KEY 	(FeeCode)	REFERENCES FEE_bxc);


--DESCRIBE STATEMENTS
DESCRIBE RATING_bxc;
DESCRIBE CATEGORY_bxc;
DESCRIBE TITLE_bxc;
DESCRIBE COPY_bxc;
DESCRIBE FEE_bxc;
DESCRIBE MEMBER_bxc;
DESCRIBE TRANSACTION_bxc;
DESCRIBE TRANS_DETAIL_bxc;

--PART II INSERT DATA

--Insert data into Rating table
INSERT INTO RATING_bxc
VALUES('PG','Parental Guidandance');

INSERT INTO RATING_bxc
VALUES('PG-13','Unappropriate Under 13');

INSERT INTO RATING_bxc
VALUES('R','Resticted Under 17');

INSERT INTO RATING_bxc
VALUES('G','General Audience');


--Insert data into Category table
INSERT INTO CATEGORY_bxc
VALUES('DR', 'Drama');

INSERT INTO CATEGORY_bxc
VALUES('AC', 'Action');

INSERT INTO CATEGORY_bxc
VALUES('CL', 'Classics');

INSERT INTO CATEGORY_bxc
VALUES('FM', 'Family');

INSERT INTO CATEGORY_bxc
VALUES('HR', 'Horror');


--Insert data into Title table
INSERT INTO TITLE_bxc
VALUES(92, 'Railway Man', 'R', 'DR');

INSERT INTO TITLE_bxc
VALUES(76, 'Terminator', 'R', 'AC');

INSERT INTO TITLE_bxc
VALUES(119, 'Divergent', 'PG-13', 'AC');

INSERT INTO TITLE_bxc
VALUES(12, 'Casa Blanca', 'PG', 'CL');

INSERT INTO TITLE_bxc
VALUES(29, 'Brave', 'PG', 'FM');

INSERT INTO TITLE_bxc
VALUES(42, 'Frozen', 'PG', 'FM');

INSERT INTO TITLE_bxc
VALUES(58, 'The Thing', 'R', 'HR');

INSERT INTO TITLE_bxc
VALUES(230, 'Lone Survivor', 'R', 'AC');

INSERT INTO TITLE_bxc
VALUES(245, 'Rio 2', 'G', 'FM');

INSERT INTO TITLE_bxc
VALUES(159, 'The Croods', 'PG', 'FM');

INSERT INTO TITLE_bxc
VALUES(240, 'Butterfly Effect', 'R', 'DR');

INSERT INTO TITLE_bxc
VALUES(218, 'Gone With The Wind', 'PG', 'CL');

INSERT INTO TITLE_bxc
VALUES(280, 'Sabotage', 'R', 'AC');

INSERT INTO TITLE_bxc
VALUES(299, 'Oculus', 'R', 'HR');


--Insert data into Copy table
INSERT INTO COPY_bxc
VALUES(215, 92, 'DVD');

INSERT INTO COPY_bxc
VALUES(191, 76, 'DVD');

INSERT INTO COPY_bxc
VALUES(259, 119, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(89, 12, 'DVD');

INSERT INTO COPY_bxc
VALUES(96, 29, 'DVD');

INSERT INTO COPY_bxc
VALUES(152, 42, 'DVD');

INSERT INTO COPY_bxc
VALUES(86, 58, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(260, 119, 'DVD');

INSERT INTO COPY_bxc
VALUES(301, 230, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(376, 245, 'DVD');

INSERT INTO COPY_bxc
VALUES(153, 42, 'DVD');

INSERT INTO COPY_bxc
VALUES(202, 159, 'DVD');

INSERT INTO COPY_bxc
VALUES(402, 240, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(381, 218, 'DVD');

INSERT INTO COPY_bxc
VALUES(419, 280, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(203, 159, 'DVD');

INSERT INTO COPY_bxc
VALUES(302, 230, 'DVD');

INSERT INTO COPY_bxc
VALUES(375, 245, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(421, 299, 'DVD');

INSERT INTO COPY_bxc
VALUES(299, 29, 'DVD');


--Insert data into Fee table
INSERT INTO FEE_bxc
VALUES('A', 3.00);

INSERT INTO FEE_bxc
VALUES('B', 2.00);


--Insert data into Member table
INSERT INTO MEMBER_bxc
VALUES(23, 'John', 'Smith', '9725551212');

INSERT INTO MEMBER_bxc
VALUES(102, 'Doug', 'Miller', '2145552345');

INSERT INTO MEMBER_bxc
VALUES(154, 'Jackie', 'Brown', '8175552345');

INSERT INTO MEMBER_bxc
VALUES(83, 'Mike', 'Norton', NULL);

INSERT INTO MEMBER_bxc
VALUES(53, 'Heather', 'Johnson', '2145551534');

INSERT INTO MEMBER_bxc
VALUES(68, 'Anthony', 'Smith', NULL);

INSERT INTO MEMBER_bxc
VALUES(72, 'Mike', 'Jones', '9725551212');


--Insert data into Transaction table
INSERT INTO TRANSACTION_bxc
VALUES(1, '02-September-2014', 23);

INSERT INTO TRANSACTION_bxc
VALUES(2, '02-September-2014', 102);

INSERT INTO TRANSACTION_bxc
VALUES(3, '02-September-2014', 154);

INSERT INTO TRANSACTION_bxc
VALUES(4, '03-September-2014', 83);

INSERT INTO TRANSACTION_bxc
VALUES(5, '03-September-2014', 23);

INSERT INTO TRANSACTION_bxc
VALUES(6, '04-September-2014', 83);

INSERT INTO TRANSACTION_bxc
VALUES(7, '04-September-2014', 154);

INSERT INTO TRANSACTION_bxc
VALUES(8, '05-September-2014', 53);

INSERT INTO TRANSACTION_bxc
VALUES(9, '05-September-2014', 68);

INSERT INTO TRANSACTION_bxc
VALUES(10, '05-September-2014', 23);

INSERT INTO TRANSACTION_bxc
VALUES(11, '05-September-2014', 72);


--Insert data into Transaction Detail table
INSERT INTO TRANS_DETAIL_bxc
VALUES(1, 215, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(1, 191, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(2, 259, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(3, 89, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(3, 96, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(3, 152, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(4, 86, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(5, 260, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(6, 301, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(7, 376, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(7, 153, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(8, 202, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(8, 402, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(9, 381, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(9, 419, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(10, 203, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(10, 302, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(11, 375, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(11, 421, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(11, 299, 'A');

--SELECT STATEMENTS
SELECT * FROM RATING_bxc;
SELECT * FROM CATEGORY_bxc;
SELECT * FROM TITLE_bxc;
SELECT * FROM COPY_bxc;
SELECT * FROM FEE_bxc;
SELECT * FROM MEMBER_bxc;
SELECT * FROM TRANSACTION_bxc;
SELECT * FROM TRANS_DETAIL_bxc;


--PART III MODIFY TABLES

--Modify the MEMBER_bxc table

--Change last name of MEMBER 154 to 'TURNER'
UPDATE MEMBER_bxc
SET MemberLName = 'Turner'
WHERE MemberID = '154';

--Change phone number of MEMBER 23 to '2146881234'
UPDATE MEMBER_bxc
SET MemberPhone = '2146881234'
WHERE MemberID = '23';

--Add Member 100 (Amanda Green, no phone number)
INSERT INTO MEMBER_bxc
VALUES(100, 'Amanda', 'Green', NULL);


--Modify the TITLE_bxc table

--Add a new title:
INSERT INTO TITLE_bxc
VALUES(279, 'Hidalgo', 'PG-13', 'DR');


--Modify the COPY_bxc table

--Add  new copies:
INSERT INTO COPY_bxc
VALUES(327, 92, 'DVD');

INSERT INTO COPY_bxc
VALUES(382, 218, 'BLU-RAY');

INSERT INTO COPY_bxc
VALUES(406, 279, 'DVD');


--Modify Transaction table
INSERT INTO TRANSACTION_bxc
VALUES(12, '06-September-2014', 53);

INSERT INTO TRANSACTION_bxc
VALUES(13, '07-September-2014', 100);


--Modify Transaction Detail table
INSERT INTO TRANS_DETAIL_bxc
VALUES(12, 376, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(12, 406, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(13, 382, 'A');

INSERT INTO TRANS_DETAIL_bxc
VALUES(13, 215, 'B');

INSERT INTO TRANS_DETAIL_bxc
VALUES(13, 327, 'A');

--Change the Fee Code of CopyID 215 to 'B'
UPDATE TRANS_DETAIL_bxc
SET FeeCode = 'B'
WHERE CopyID = 215 AND TransID = 1;


SELECT * FROM MEMBER_bxc;
SELECT * FROM TITLE_bxc;
SELECT * FROM COPY_bxc;
SELECT * FROM TRANSACTION_bxc;
SELECT * FROM TRANS_DETAIL_bxc;

--PROJECT #3 PART B


--a. Altering Rating_bxc table to enable up to 35 chars
ALTER TABLE RATING_bxc
MODIFY (RatingDesc VARCHAR(35));

--Updating tabe Rating_bxc
UPDATE RATING_bxc 
SET RatingDesc = 'Not Suitable for Children Under 13'
WHERE Rating = 'PG-13';

--b. Add row into FEE table
INSERT INTO FEE_bxc
VALUES ('D', 1.00);

--Q1.
SELECT TransID as Trans_ID, CopyID as Copy_ID, FeeCode
FROM TRANS_DETAIL_bxc
ORDER BY Trans_ID ASC,  Copy_ID ASC;

--Q2
SELECT TITLE_bxc.TitleID, Title, COUNT(DISTINCT Format)
FROM TITLE_bxc, COPY_bxc
WHERE TITLE_bxc.TitleID = COPY_bxc.TitleID
GROUP BY (TITLE_bxc.TitleID, Title);

--Q3
SELECT MemberID as Member_ID, MemberFName as First_Name,
       MemberLName as Last_Name, '('||SUBSTR(MemberPhone, 1,3)||')'||
				 SUBSTR(MemberPhone, 4,3)||'-'||
				 SUBSTR(MemberPhone, 7,4) as Phone
FROM MEMBER_bxc
ORDER BY MemberID ASC;

--Q4
SELECT TITLE_bxc.CatID as CatID, 
CatName as Category, 
TITLE_bxc.TitleID as TitleID, Title, 
TO_CHAR(FEE_bxc.FeeAmt,'$9.99') AS Fee 
FROM TITLE_bxc
INNER JOIN CATEGORY_bxc ON TITLE_bxc.CatID = CATEGORY_bxc.CatID
INNER JOIN COPY_bxc ON TITLE_bxc.TitleID = COPY_bxc.TitleID
INNER JOIN TRANS_DETAIL_bxc ON COPY_bxc.CopyID = TRANS_DETAIL_bxc.CopyID
INNER JOIN FEE_bxc ON TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode
INNER JOIN (
SELECT TRANS_DETAIL_bxc.TransID, MIN(FEE_bxc.FeeAmt) as FeeAmt FROM TRANS_DETAIL_bxc
INNER JOIN FEE_bxc ON TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode
GROUP BY TRANS_DETAIL_bxc.TransID) FeeCode ON TRANS_DETAIL_bxc.TransID = FeeCode.TransID AND FEE_bxc.FeeAmt = FeeCode.FeeAmt
ORDER BY FEE_bxc.FeeAmt;

--Q5
SELECT Title, TitleID, Rating, CatName
FROM TITLE_bxc, CATEGORY_bxc
WHERE CATEGORY_bxc.CatID = TITLE_bxc.CatID
ORDER BY CatName ASC, title ASC;

--Q6
SELECT CatName as Category_Name, 
       COUNT(TITLE_bxc.CatID) as Title_Count
FROM CATEGORY_bxc, TITLE_bxc
WHERE CATEGORY_bxc.CatID = TITLE_bxc.CatID
GROUP BY (CatName)
ORDER BY COUNT(TITLE_bxc.CatID);

--Q7
SELECT TRANSACTION_bxc.TransID, COPY_bxc.CopyID,
       Title, to_CHAR(FeeAmt, '$9.99')
FROM TRANS_DETAIL_bxc, COPY_bxc, FEE_bxc, TITLE_bxc, TRANSACTION_bxc
WHERE TRANS_DETAIL_bxc.CopyID = COPY_bxc.CopyID
AND COPY_bxc.TitleID = TITLE_bxc.TitleID
AND TRANSACTION_bxc.TransID = TRANS_DETAIL_bxc.TransID
AND TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode
AND FeeAmt < 2.50
ORDER BY FeeAmt, TITLE_bxc.TitleID;


--Q8
SELECT TRANSACTION_bxc.TransID, to_CHAR(TransDate, 'mm-dd-yyyy') as TransDate , 
MEMBER_bxc.MemberID, MemberFName, MemberLName, COUNT(CopyID)
FROM TRANSACTION_bxc, MEMBER_bxc, COPY_bxc
WHERE TRANSACTION_bxc.MemberID = MEMBER_bxc.MemberID
GROUP BY (TRANSACTION_bxc.TransID, TransDate, MEMBER_bxc.MemberID, 
          MemberLName, MemberFName)
ORDER BY TRANSACTION_bxc.TransID;

--Q9
SELECT COPY_bxc.CopyID, Title, Rating, Format, 
       to_CHAR(FeeAmt, '$99.99') as Fee
FROM COPY_bxc, TITLE_bxc, FEE_bxc, TRANS_DETAIL_bxc
WHERE TransID = 3
AND TITLE_bxc.TitleID = COPY_bxc.TitleID
AND TRANS_DETAIL_bxc.CopyID = COPY_bxc.CopyID
AND TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode
ORDER BY COPY_bxc.CopyID;

--Q10
SELECT CATEGORY_bxc.CatID, CatName, COUNT(DISTINCT Title)
FROM TITLE_bxc, CATEGORY_bxc
WHERE TITLE_bxc.CatID = CATEGORY_bxc.CatID
GROUP BY (CATEGORY_bxc.CatID, CatName)
ORDER BY CATEGORY_bxc.CatID;

--Q11
SELECT TransID, TITLE_bxc.TitleID, Title, CatName, TRANS_DETAIL_bxc.FeeCode, FeeAmt
FROM TRANS_DETAIL_bxc, TITLE_bxc, CATEGORY_bxc, FEE_bxc, COPY_bxc
WHERE TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode
AND   TITLE_bxc.CatID = CATEGORY_bxc.CatID
AND   TITLE_bxc.TitleID = COPY_bxc.TitleID
AND   COPY_bxc.CopyID = TRANS_DETAIL_bxc.CopyID
AND FeeAmt > 
(SELECT AVG(FeeAmt)
FROM FEE_bxc
INNER JOIN TRANS_DETAIL_bxc
ON TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode)
ORDER BY Title; 


--Q12
SELECT TITLE_bxc.TitleID, Title, CatName, Rating
FROM TITLE_bxc, CATEGORY_bxc, COPY_bxc, TRANS_DETAIL_bxc
WHERE TITLE_bxc.CatID = CATEGORY_bxc.CatID
AND   TITLE_bxc.TitleID = COPY_bxc.TitleID
AND   COPY_bxc.CopyID = TRANS_DETAIL_bxc.CopyID
AND   FeeCode = 'B'
ORDER BY Title;


--Q13
SELECT TRANS_DETAIL_bxc.TransID as Transaction_ID, 
TO_CHAR(TransDate,'mm/dd/yy') as Transaction_Date, 
TO_CHAR(SUM(FeeAmt),'$9.99') as Transaction_Total
FROM FEE_bxc, TRANS_DETAIL_bxc, TRANSACTION_bxc
WHERE TRANS_DETAIL_bxc.TransID = 3
AND TRANS_DETAIL_bxc.TransID = TRANSACTION_bxc.TransID
AND TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode
GROUP BY (TRANS_DETAIL_bxc.TransID, TransDate);

--Q14
SELECT TRANS_DETAIL_bxc.CopyID as Copy_ID, COPY_bxc.TitleID as Title_ID, 
Title as Title_Name, TRANS_DETAIL_bxc.FeeCode as Fee_Code, 
to_CHAR(FeeAmt, '$9.99') as Fee_Amt
FROM COPY_bxc, TITLE_bxc, FEE_bxc, TRANS_DETAIL_bxc
WHERE TRANS_DETAIL_bxc.CopyID = COPY_bxc.CopyID
AND   TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode 
AND   COPY_bxc.TitleID = TITLE_bxc.TitleID
AND   TransID = 10
AND FeeAmt =
(SELECT MAX(FeeAmt)
FROM FEE_bxc
INNER JOIN TRANS_DETAIL_bxc
ON FEE_bxc.FeeCode = TRANS_DETAIL_bxc.FeeCode);

--Q15
SELECT COPY_bxc.TitleID as Title_ID, Title as Title_Name, 
TITLE_bxc.CatID as Category_ID, CatName as Category_Name, 
to_CHAR(FeeAmt, '$9.99') as Fee_Amt
FROM  TRANS_DETAIL_bxc, FEE_bxc, COPY_bxc, TITLE_bxc, CATEGORY_bxc
WHERE TRANS_DETAIL_bxc.CopyID = COPY_bxc.CopyID
AND   TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode 
AND   COPY_bxc.TitleID = TITLE_bxc.TitleID
AND   TITLE_bxc.CatID = CATEGORY_bxc.CatID
AND   TransID = 8
AND FeeAmt =
(SELECT MIN(FeeAmt)
FROM FEE_bxc
INNER JOIN TRANS_DETAIL_bxc
ON FEE_bxc.FeeCode = TRANS_DETAIL_bxc.FeeCode);

--16
SELECT TRANS_DETAIL_bxc.CopyID, COPY_bxc.TitleID, Title,
to_CHAR(FeeAmt, '$9.99') as Fee_Amt
FROM  COPY_bxc, TITLE_bxc, FEE_bxc, TRANS_DETAIL_bxc
WHERE TRANS_DETAIL_bxc.CopyID = COPY_bxc.CopyID
AND   TRANS_DETAIL_bxc.FeeCode = FEE_bxc.FeeCode 
AND   COPY_bxc.TitleID = TITLE_bxc.TitleID  
AND FeeAmt >
(SELECT AVG(FeeAmt)
FROM FEE_bxc
INNER JOIN TRANS_DETAIL_bxc
ON FEE_bxc.FeeCode = TRANS_DETAIL_bxc.FeeCode)
ORDER BY FeeAmt, COPY_bxc.CopyID;

--Q17
SELECT TRANSACTION_bxc.MemberID as Member_ID, MemberFName as First_Name,
MemberLName as Last_Name, to_CHAR(SUM(FeeAmt), '$99.99' ) as Fee_Total
FROM MEMBER_bxc, TRANS_DETAIL_bxc, TRANSACTION_bxc, FEE_bxc
WHERE TRANS_DETAIL_bxc.TransID = TRANSACTION_bxc.TransID
AND   TRANSACTION_bxc.MemberID = MEMBER_bxc.MemberID
AND   TRANSACTION_bxc.MemberID = 23
GROUP BY(TRANSACTION_bxc.MemberID, MemberFName, MemberLName);


--Q18
SELECT TransID, TransDate, TRANSACTION_bxc.MemberID, MemberFName, MemberLName, 
('(' || SUBSTR(MemberPhone,1,3) || ') ' || SUBSTR(MemberPhone,4,3) || '-' || SUBSTR(MemberPhone,7,4)) AS MemberPhone 
FROM TRANSACTION_bxc, MEMBER_bxc
WHERE TRANSACTION_bxc.MemberID = MEMBER_bxc.MemberID
AND   TransDate >= '04-September-2014'
ORDER BY TransDate, MEMBER_bxc.MemberID;


--Q19
SELECT  MemberID as Member_ID, 
MemberFName as First_Name, MemberLName as Last_Name 
FROM MEMBER_bxc
WHERE MemberFName LIKE 'J%'
OR MemberLName LIKE 'J%'
ORDER BY MemberLName;

--Q20
SELECT  MEMBER_bxc.MemberID as Member_ID, 
MemberFName as First_Name, 
MemberLName as Last_Name, 
COUNT(TRANS_DETAIL_bxc.TransID) as Transaction_Count 
FROM MEMBER_bxc
INNER JOIN TRANSACTION_bxc ON MEMBER_bxc.MemberID = TRANSACTION_bxc.MemberID
INNER JOIN TRANS_DETAIL_bxc ON TRANSACTION_bxc.TransID = TRANS_DETAIL_bxc.TransID
GROUP BY MEMBER_bxc.MemberID, MemberFName, MemberLName
ORDER BY Transaction_Count DESC, MEMBER_bxc.MemberID DESC;












































