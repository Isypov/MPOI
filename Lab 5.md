
```r
html = read_html("http://www.imdb.com/search/title?count=100&release_date=2017,2017&title_type=feature")
              #вміст   #знах всі 1ранк
rank_data <- html_text(html_nodes(html,'.text-primary'))
             #претворити в числа текст ранку       
rank_data = as.numeric(rank_data)
               
title_data <- html_text(html_nodes(html,'.lister-item-header a'))
runtime_data <- html_text(html_nodes(html,'.text-muted .runtime'))
                           # заміна min на пустоту
runtime_data = as.numeric(gsub(" min", "", runtime_data))
movies <- data.frame(Rank = rank_data, Title = title_data, Runtime = runtime_data, stringsAsFactors = FALSE)
```

# 1.	Виведіть перші 6 назв фільмів дата фрейму.
```{r}
head(movies, 6)$Title
[1] "Зорянi вiйни: Останнi Джедаi"   "The Disaster Artist"            "The Shape of Water"             "Лiга справедливостi"           
[5] "Jumanji: Welcome to the Jungle" "Тор: Рагнарок"
```

# 2.	Виведіть всі назви фільмів с тривалістю більше 120 хв.
```{r}
# зробити підмножину
subset(movies, Runtime > 120)$Title
[1] "Зорянi вiйни: Останнi Джедаi"             [12] "Валерiан i мiсто тисячi планет"           [23] "Вiйна за планету мавп"                           
[2] "The Shape of Water"                       [13] "Логан: Росомаха"                          [24] "Mudbound"                    
[3] "Тор: Рагнарок"                            [14] "Phantom Thread"                           [25] "The Square"                           
[4] "Mother!"                                  [15] "Downsizing"                               [26] "Roman J. Israel, Esq."            
[5] "Kingsman: Золоте кiльце"                  [16] "Диво-Жiнка"                               [27] "Пiрати Карибського моря: Помста Салазара"                             
[6] "Вартовi Галактики 2"                      [17] "Людина-павук: Повернення додому"          [28] "Трансформери: Останнiй лицар"                                
[7] "Воно"                                     [18] "Detroit"                                  [29] "Пострiл в безодню"                            
[8] "The Killing of a Sacred Deer"             [19] "All the Money in the World"               [30] "Power Rangers"                      
[9] "Darkest Hour"                             [20] "Molly's Game"                             [31] "Hostiles" 
[10] "Call Me by Your Name"                    [21] "Сiм сестер"                               [32] "Girls Trip"                           
[11] "Той, хто бiжить по лезу 2049"            [22] "Красуня i Чудовисько"                     [33] "Джон Уiк 2" 
```

# 3.	Скільки фільмів мають тривалість менше 100 хв.
```{r}
     
nrow(movies[movies$Runtime < 100, ])
[1] 20
```
