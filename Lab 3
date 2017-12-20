#1.	За допомогою download.file() завантажте любий excel файл з порталу http://data.gov.ua та зчитайте його (xls, xlsx – бінарні формати, тому встановить mode = “wb”. Виведіть перші 6 строк отриманого фрейму даних.

```r
> Sys.setlocale(locale = "ukrainian")
[1] "LC_COLLATE=Ukrainian_Ukraine.1251;LC_CTYPE=Ukrainian_Ukraine.1251;LC_MONETARY=Ukrainian_Ukraine.1251;LC_NUMERIC=C;LC_TIME=Ukrainian_Ukraine.1251"

> fileURL <- "http://data.gov.ua/file/153458/download?token=_qZ4XYiT"
  > download.file(fileURL, destfile = "data.xls", mode = "wb")
trying URL 'http://data.gov.ua/file/153458/download?token=_qZ4XYiT'
Content type 'application/vnd.ms-excel' length 42496 bytes (41 KB)
downloaded 41 KB
                                                                     #якщо зедер тру то перший рядок це заголовок
> data <- read.xlsx("data.xls", sheetIndex = 1, encoding = "UTF-8", header = TRUE)
> head(data)
  Інформація.про.фінансування.видатків.обласного.бюджету.Рівненської.області..загальний.фонд.                 NA.
1                                                                        станом на 14.12.2017                <NA>
2                                                                                        <NA>                <NA>
3                                                                                         Код        Найменування
4                                                                                        0100 Державне управління
5                                                                                        1000              Освіта
6                                                                                        2000    Охорона здоров'я
                       NA..1                         NA..2                            NA..3            NA..4            NA..5
1                       <NA>                          <NA>                             <NA>             <NA>             <NA>
2                       <NA>                          <NA>                             <NA>             <NA>       (тис.грн.)
3 Уточнений  розпис на рік   Уточнений розпис на 12 міс.   Всього профінсовано  14.12.2017      % до 12 міс.        % до року
4                    10885.3                       10885.3                      10052.63244 92.3505318181401 92.3505318181401
5                526346.4714                   526346.4714                     490617.82059 93.2119520598348 93.2119520598348
6               781978.88179                  781978.88179                      703181.5649  89.923344642041  89.923344642041
```

#2.	За допомогою download.file() завантажте файл getdata_data_ss06hid.csv за посиланням https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv та завантажте дані в R. Code book, що пояснює значення змінних знаходиться за посиланням https://www.dropbox.com/s/dijv0rlwo4mryv5/PUMSDataDict06.pdf?dl=0  Необхідно знайти, скільки property мають value $1000000+

```r
> download.file("https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv", destfile = "data.csv")
trying URL 'https://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Fss06hid.csv'
Content type 'text/csv' length 4246554 bytes (4.0 MB)
downloaded 4.0 MB
> data <- read.csv("data.csv")
> values <- data$VAL
         list-spisok                            #! зворотне. превіряємо чи є НА 
  > a <- lapply(values, function(x) if (!is.na(x) && x==24) TRUE else NA)
> length(a[!is.na(a)])
[1] 53
```

#3.	Зчитайте xml файл за посиланням http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml Скільки ресторанів мають zipcode 21231?

```r
> url <- "http://d396qusza40orc.cloudfront.net/getdata%2Fdata%2Frestaurants.xml"
         #фун будує дерево   коп през
> doc <- xmlTreeParse(url,useInternal=TRUE)
 #знаходимо кореневий ел
> rootNode <- xmlRoot(doc)
         #спец мова для запитів шукаємо рядок врядку текст в якому= 21231
> length(xpathApply(rootNode, '//row/row/zipcode[text()="21231"]'))
[1] 127
```
