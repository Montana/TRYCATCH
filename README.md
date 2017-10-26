# TRYCATCH
List of medications on the WHO list. Written by Montana Mendy. I've attached the list of medications, so you can search them via sql. Inspiration for the name TRYCATCH comes from the following: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch. Information from: http://www.who.int/medicines/publications/essentialmedicines/en/

Let's get started

   ```mysql
   BEGIN TRY
   -- execute each statement
   INSERT INTO MEDICATIONS(PK) VALUES ('medications')
   INSERT INTO MEDICATIONS(PK) VALUES ('who')
   ```
   Should print out 

```mysql
+----+------------------------------------------------------------------------------+
| PK |                                 Medications                                  |
+----+------------------------------------------------------------------------------+
|  1 | NAPROXEN, neurontin, DOCUSATE, HYDROCODONE, BACLOFEN, advil                  |
|  2 | celexa, lortab, lyrica, ambien, xanax                                        |
|  3 | adipex                                                                       |
|  4 | opana, roxicodone                                                            |
|  5 | adderall                                                                     |
|  6 | hydrocodone/apap                                                             |
|  7 | NEXIUM, METOPROLOL, lipitor, VERAPAMIL, ASPIRIN, WARFARIN, ambien            |
|  8 | prozac                                                                       |
|  9 | flexeril                                                                     |
| 10 | soma, LITHIUM, MULTI-VITAMIN, fentanyl patch, percocet, PROPANOLOL, tegretol |
+----+------------------------------------------------------------------------------+
```

If you want this in a organized list, and not a table, for example 

```mysql
 NAPROXEN
 neurontin
 DOCUSATE
 HYDROCODONE
 BACLOFEN
 advil
 celexa
 lortab
 lyrica
 ambien
 xanax
 adipex
 opana
 ```
 
 You can run these variables 
 ```mysql
 SELECT  DISTINCT
 LTRIM(RTRIM(SUBSTRING(Medications, Number ,CHARINDEX(',', Medications + ',', Number ) - Number))) AS Medication 
 FROM @Medications 
 JOIN master..spt_values ON Number <= DATALENGTH(Medications) + 1  AND type='P'
 AND SUBSTRING(',' + Medications, Number , 1) = ',' 
 ```
 
 If you can output it to awk 
  ```mysql
 outputcommand | awk 'BEGIN{FS="|"}{print $3}'|awk 'BEGIN{RS=","}{print $0}'
  ```
  
  That might be easier, given your circumstances. 
