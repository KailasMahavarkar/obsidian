
# (+)
#### match as many as you can but at-least match one

string: 
```
regex: 
/ca+/g

string:
A fat cat ran down the street,
it was searching for food to eat
caaaaaat is brown
```

result:
![](https://i.imgur.com/oYWX5eT.png)



# (?) -> Optional

```
regex: 
/ca+t? */g

string:
A fat cat     ran down the street,
it was searching for food to eat
caaaaaat is brown
```

![](https://i.imgur.com/7CjbBon.png)


# (\*) -> match 0 or more and its optional

```
regex: 
/re*/g

string:
A fat cat     ran down the street,
it was searching for food to eat
caaaaaat is brown
```

![](https://i.imgur.com/XIzHlhr.png)


> Q) so what is difference between (+) and (\*)
> --> well in (\*) case it will match 1st character and 2nd will be optional thus... its matching all 'r' but in case of (+) its must to have prev characters

![](https://i.imgur.com/MUfKqBC.png)




----
#regex

