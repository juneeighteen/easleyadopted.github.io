---
layout: default
title: Easley Adopted Me 
description: “As soon as I saw you, I knew an adventure was going to happen.” --Winnie the Pooh
imageURL: /images/sharedname.jpg
---      


<script>
    

    var nameKey = Cookies.get('eamnamekey') || "standard";
    nameKey = nameKey.replace(/\W/g, '') //sanitize

    $.getJSON( "data/" + nameKey + ".json", function( data ) {
//        $.getJSON( "data/blankkey.json", function( data ) {

      var objDataFN = {
          "class": "bl1",
          html: data.first 
      };

      var objDataMN = {
          "class": "blocky bl2",
          html: data.middle
      };

      var className = "";
      var nocolorClassName = "blnc";
      


      for (l in data.first) {

          var letterObject = {

          };
        var thisLetter = data.first[l];
        if (["+"].indexOf(thisLetter) >= 0) {
            className = nocolorClassName;
            
        } else {
            className = "bl" + (l % 6);
        }
        letterObject.class = "blocky " + className;
        letterObject.html = thisLetter;
        $("<span/>", letterObject).appendTo(".fname");
//        console.log(thisLetter, className, l, l%3);


      };



      for (l in data.middle) {

          var letterObject = {

          };
        var thisLetter = data.middle[l];
        if (["+"].indexOf(thisLetter) >= 0) {
            className = nocolorClassName;
            
        } else {
            className = "bl" + (l % 6);
        }
        letterObject.class = "blocky " + className;
        letterObject.html = thisLetter;
        $("<span/>", letterObject).appendTo(".mname");
//        console.log(thisLetter, className, l, l%3);


      };


        



 
});
</script>


<div class="container">
<div class="home">
    <div class="banner">
        <div class="banner-text">
            <h1 class="headline"><span class="blocky tlt fname"></span></h1>
            <h1 class="headline"><span class="blocky tlt mname"/></h1>
            <h3 class="quotefont">“As soon as I saw you, I knew an adventure was going to happen.”</h3>
            <h3 class="quotefont"><i>-- Winnie the Pooh</i></h3>
            <br/>
            <h3 class="quotefont">Pure and genuine religion in the sight of God the Father means caring for orphans and widows...</h3>
            <h3 class="quotefont"><i>-- James 1:27a NLT</i></h3>
            <br/>
        </div>

        
        
            

    </div>      


                  
</div>
</div>

