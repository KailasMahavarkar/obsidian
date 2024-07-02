Multiple Approaches
1. we can use type=month and we can get both month and date from it
```html
<!DOCTYPE html>
<html>
<head>
  <title>Month and Year Selector</title>
</head>
<body>
  <div>
    <label for="month">Month and Year:</label>
    <input type="month" id="month" name="month" />
  </div>
  <div>
    <button onclick="clearSelection()">Clear Selection</button>
  </div>

  <script>
    function clearSelection() {
      document.getElementById('month').value = '';
    }
  </script>
</body>
</html>

```

2. we can use two select inputs 
   -> one select for range year (1923-2023)
   -> one select for month

3. custom component (reference reactdatepicker - Custom Month)
