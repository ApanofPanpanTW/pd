<!DOCTYPE html>
<!-- goto line 81 and be sure to edit your information -->
<html>
    <head>
        <script src="https://code.jquery.com/jquery.min.js"></script>
        <link href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/css/bootstrap.min.css" rel="stylesheet" type="text/css" />
        <script src="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.6/js/bootstrap.min.js"></script>
        <link href="https://netdna.bootstrapcdn.com/font-awesome/4.0.3/css/font-awesome.min.css" rel="stylesheet" type="text/css" />
        <link href="https://fonts.googleapis.com/css?family=Share+Tech+Mono&effect=outline" rel="stylesheet" type="text/css"> 
    
        <style>
            body { 
                background-color: rgba(0, 0, 0, 0); 
                margin: 0px auto; 
                overflow: hidden; 
                font-family: 'Cast W01 Medium', monospace;
                font-size: 13px;
                color: #F8F8FF;
            }

            .Blink {
                animation: blinker 1.5s cubic-bezier(.5, 0, 1, 1) infinite alternate;  
            }

            @keyframes blinker {  
                from { opacity: 1; }
                to { opacity: 0; }
            }

            .top-right{
                float: right;
                width: auto;
                text-align: right;
            }
            
            .top-right-container{
                float: right;
                width: auto;
                text-align: right;
                /* edit the fourth value of the next line to change opacity */
                /* 0.0 is clear, 1.0 is completely opaque                   */
                background-color: rgba(0,0,0,0.5);
                padding: 5px;
                margin: 10px;
                -moz-border-radius: 10px;
                -webkit-border-radius:10px;
                border-radius:10px;
            }

            .container{
                width: 100wh;
                height: 100vh;
            }
        </style>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width">
        <title>Axon Bodycam Overlay</title>
    </head>

    <body>
        <div class="top-right-container">
            <div class="https://www.viveport.com/media/catalog/product/cache/dd44ab9591c40efc99bce320df9a7888/6/1/614e9355-6dee-47b7-82be-78bc4a8ba047.1dc307fe.png">
                <img src="https://irp-cdn.multiscreensite.com/7cd7b965/dms3rep/multi/mobile/logo-03.png" width="64" height="64" border="0">
            </div>
            <div class="top-right">
                REC&nbsp;<i class="fa fa-circle text-danger Blink"></i>&nbsp;&nbsp;Axon Body Cam&trade;&nbsp;&nbsp;<br />
                <span id="player">XXX</span>
                <span id="callsign">[000]</span>&nbsp;&nbsp;<br />
                <span id="agency">XXX</span>&nbsp;&nbsp;<br />                
                <span style="padding:0px;margin:0px;" id="month">XXX</span>
				<span style="padding:0px;margin:0px;" id="day">00</span>
                <span style="padding:0px;margin:0px;" id="year">0000</span>&nbsp;
                <span style="padding:0px;margin:0px;" id="hr">00</span>
                <span style="padding:0px;margin:0px;">:</span>
                <span style="padding:0px;margin:0px;" id="min">00</span>
                <span style="padding:0px;margin:0px;">:</span>
                <span style="padding:0px;margin:0px;" id="sec">00</span>
                <span style="padding:0px;margin:0px;" id="tz">XX</span>&nbsp;&nbsp;
            </div>
        </div>
    </body>
    
    <script>
        //***edit this only for your information***
        const player = "二級警員";
        const agency = "神奈川警政署";
        const callsign = "[728]";
        //***        end edit this only         ***
    
        var d,h,m,s,animate;
        const monthNames = ["JAN","FEB","MAR","APR","MAY","JUN","JUL","AUG","SEP","OCT","NOV","DEC"];

        function init(){
            d=new Date();
            h=d.getHours();
            m=d.getMinutes();
            s=d.getSeconds();
            t=d.toLocaleString('en', {timeZoneName:'short'}).split(' ').pop();
            clock();
            month=d.getMonth();
            day=d.getDate();
            year=d.getFullYear();
            
        };

        function clock(){
            s++;
            if(s==60){
                s=0;
                m++;
                if(m==60){
                    m=0;
                    h++;
                    if(h==24){
                        h=0;
                    }
                }
            }
            $('sec', s);
            $('min', m);
            $('hr', h);
            $('tz', t);
            $('month', monthNames[month]);
            $('day', day);
            $('year', year);
            $('player', player);
            $('agency', agency);
            $('callsign', callsign);
            animate=setTimeout(clock,1000);
        };

        function $(id,val){
            if(val<10){
                val='0'+val;
            }
            document.getElementById(id).innerHTML=val;
        };

        window.onload=init;
    </script>

</html>
