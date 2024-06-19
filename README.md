<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Simple Calculator Table</title>
    <style>
        body {
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
            background-color: #f0f0f0;
        }
        table {
            border-collapse: collapse;
            width: 200px;
            height: 300px;
        }
        td {
            border: 1px solid #333;
            text-align: center;
            vertical-align: middle;
            font-size: 2em;
            background-color: #fff;
            width: 25%;
            height: 25%;
        }
        .empty {
            background-color: #e0e0e0;
        }
    </style>
</head>
<body>
    <table>
        <tr>
            <td>1</td>
            <td>2</td>
            <td>3</td>
        </tr>
        <tr>
            <td>4</td>
            <td>5</td>
            <td>6</td>
        </tr>
        <tr>
            <td>7</td>
            <td>8</td>
            <td>9</td>
        </tr>
        <tr>
            <td class="empty"></td>
            <td>0</td>
            <td class="empty"></td>
        </tr>
    </table>
</body>
</html>
