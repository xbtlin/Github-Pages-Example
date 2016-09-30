

<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8">
    <title>JS Bin</title>
    <link rel="stylesheet" type="text/css" href="css/discount.css">
    <script src="//cdn.bootcss.com/echarts/3.2.3/echarts.js"></script>
    <script src="//cdn.bootcss.com/jquery/3.1.0/jquery.js"></script>
    <script src="js/discount.js"></script>

</head>
<body>
<div>
    <div class="box" id="b1">
        <!--<div class="key"></div>-->
        <div class="value" id="discount_num"></div>
    </div>
    <div class="box" id="b2">
        <!--<div class="key"></div>-->
        <div class="value" id="v2"></div>
    </div>
    <div class="box" id="b3">
        <!--<div class="key"></div>-->
        <div class="value" id="v3"></div>
    </div>
    <div class="box" id="b4">
        <!--<div class="key"></div>-->
        <div class="value" id="v4"></div>
    </div>
</div>
<!--<div>-->
    <!--<div class="right-container">-->
        <!--<div class="content" id="trend_img"></div>-->
    <!--</div>-->
<!--</div>-->

<script style="text/javascript">
    $(function(){
        getSumAndTrend();
    })
</script>

</body>
</html>




