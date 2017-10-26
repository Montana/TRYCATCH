# TRYCATCH
List of medications on the WHO list. Written by Montana Mendy. I've attached the list of medications, so you can search them via sql. 

   ```mysql
   BEGIN TRY
   -- execute each statement
   INSERT INTO MEDICATIONS(PK) VALUES ('medications')
   INSERT INTO MEDICATIONS(PK) VALUES ('who')
   ```

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
