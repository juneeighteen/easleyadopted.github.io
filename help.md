---
layout: default
title: How you can help
description: “As soon as I saw you, I knew an adventure was going to happen.” --Winnie the Pooh

---      
<br/><br/><br/><br/>
<div class="container">

<div class="jumbotron">
<h1 class="fancyfont">How you can help</h1>
</div>

<script>

    var urlParams;
(window.onpopstate = function () {
    var match,
        pl     = /\+/g,  // Regex for replacing addition symbol with a space
        search = /([^&=]+)=?([^&]*)/g,
        decode = function (s) { return decodeURIComponent(s.replace(pl, " ")); },
        query  = window.location.search.substring(1);

    urlParams = {};
    while (match = search.exec(query))
       urlParams[decode(match[1])] = decode(match[2]);
})();


$.getJSON( "data/actions.json", function( data ) {


    
    for (i in data.actions) {
        
        if (i % 6 == 0) {
            if (i!= 0) {
                //End the last row
                $("</div>").appendTo("#actionContainer");
            } 

            $("<div class='row'>").appendTo("#actionContainer");

        }
        let thisAction = data.actions[i];

        if (thisAction.slug in urlParams) {
        window.location = thisAction.link;
       }

        $(panel(thisAction['name'], thisAction['url'], thisAction['link'])).appendTo('#actionContainer');

       
        console.log(thisAction);
    }

});

function panel(title, imageSrc, link) {
    
    //Create our image


    let imgAttributes = {
        class: "img img-responsive full-width",
        src: imageSrc
       
    };


    let imgTag = $("<img/>", imgAttributes);

    let imgLink = {
        href: link,
        html: imgTag,
        target: "_blank"
    };

    let imgLinkTag = $("<a>/", imgLink);


    let imgDiv = $("<div/>", { class: "image", html: imgLinkTag});

    let pnlBodyAttributes = {
        class: "panel-body",
        html: imgDiv
    }

    let lnkAttributes = {
        href: link,
        target: "_blank",
        html: title

    };

    let lnkTag = $("<a/>", lnkAttributes);

    let pnlFooterAttributes= {
        class:"panel-footer",
        html: lnkTag
    };

    
    let pnlBodyTag = $("<div/>", pnlBodyAttributes);
    let pnlFooterTag = $("<div/>", pnlFooterAttributes);

    let panelFooter = $(pnlFooterTag);
    //let myPanelContents = $(pnlFooterTag).appendTo($(pnlBodyTag));
    let myPanelContents = [$(pnlBodyTag), $(pnlFooterTag)];

    let pnlAttributes = {
        class: "panel panel-default",
        html: myPanelContents
    };

    let myPanel = $("<div/>", pnlAttributes);

    let myColAttributes = {
        class: "col-md-2",
        html: myPanel
    };

    let myActionItem = $("<div/>", myColAttributes);

    return (myActionItem);





}

</script>
<div id="actionContainer">
  
 
</div>


</div>

<!---<div class="col-md-4">
        <div class="panel panel-default">
        <div class="panel-body">
            <img class="media-object" src="#"/>
        </div>
        <div class="panel-footer">Some Action</div>
    </div>
    -->