# TRYCATCH

## What is TryCatch? 

This is public documentiation, for a private project that myself and somebody else is working on. The reason I made this documentation public, is as usual for when I make things public, is our solution process. I want to share with people how we solve problems, and give them insight to the project a little bit. 

List of select medications on the WHO list. Written by Montana Mendy. The list in it's entirety can be viewed here: http://www.who.int/medicines/publications/essentialmedicines/en/. By no means, this is every medication. This is just the beginning of an webapp I'm building in a private repo, where say you search say the following 

<pre>antihistamine</pre> 

You'd get back results of antihistamines, via 

   ```mysql
      diphenhydramine
      hydroxyzine
   ```
   
   Another example would be 
   
   <pre>benzodiazepine</pre>
   
   Then output would be
   
  ```mysql  
   alprazolam (Xanax, Xanax XR)
   clobazam (Onfi)
   clonazepam (Klonopin)
   clorazepate (Tranxene)
   chlordiazepoxide (Librium)
   diazepam (Valium, Diastat Acudial, Diastat)
   lorazepam (Ativan)
```

I've attached the list of medications, so you can search them via sql. Inspiration for the name TRYCATCH comes from the following: https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch. In this example I'm using Transact-SQL.

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
