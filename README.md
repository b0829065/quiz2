<html>
<h1>cgu 貓貓牆 </h1>
<div id="contain"></div>
<div id="contain"></div>
    <script type="text/javascript" src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.1.0/jquery.min.js">
</script>
</html>

<script>
    var tags = "cat";
    var dataUrl = "https://api.flickr.com/services/feeds/photos_public.gne?tags=" + tags + "&tagmode=any&format=json&per_page=400&jsoncallback=?";
    var data = $.getJSON(dataUrl);
    
    data.done(function(msg){
        var json = JSON.stringify(msg)
        for (var i = 0; i < msg["items"].length; i++){
            console.log(msg["items"][i]["media"]["m"])
            $("#contain").html()
            $("#contain").append($("<img/>").attr("src", msg["items"][i]["media"]["m"]))
        }
    });
    // $.each(msg.items,function(i,item){
    //            $("#contain").html();
    //            $("#contain").append($("<img/>").attr("scr",items.media.m));
    //        });
    //    });
    data.fail(function(msg){
        console.log(msg);
        $("#contain").html("fail getting data");
    });
</script>
