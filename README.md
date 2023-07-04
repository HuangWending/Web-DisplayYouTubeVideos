# Web-DisplayYouTubeVideos
Web前端(HTML和JavaScript)网页显示我的YouTube视频
<!DOCTYPE html>

这是一个HTML文档的声明，指定文档的类型为HTML。

<html>

开始一个HTML文档。


<head>

这是HTML文档的头部部分，用于包含元数据和引用外部资源。


<meta charset="UTF-8">

指定文档的字符编码为UTF-8，确保正确显示和处理文档中的文本内容。


<title>YouTube视频</title>

设置文档的标题为"YouTube视频"，该标题将显示在浏览器的标题栏中。

<style>
    #video-container {
        display: flex;
        flex-direction: column;
        align-items: center;
    }
</style>

定义内部样式表，指定`video-container`元素的样式。该样式将使其以列的方式排列，并在垂直方向上居中对齐。

</head>

头部部分的结束标签。

<body>

开始HTML文档的主体部分。

<div id="video-container"></div>

创建一个`div`元素，并指定其id为"video-container"。该元素将用于容纳视频。


<script>

这是JavaScript代码的起始标签，用于插入JavaScript代码。

var videoUrls = [
    "https://www.youtube.com/watch?v=_pcoBxzXRM4&t=8s",
    "https://www.youtube.com/watch?v=-O5vZ2mT1qs&t=1s",
    "https://www.youtube.com/watch?v=Qax-p_IKNcU",
    "https://www.youtube.com/watch?v=h5vOTuhMRzc",
    "https://www.youtube.com/watch?v=BpNgo7i8w4Y"
];

创建一个名为`videoUrls`的变量，并将一个包含5个YouTube视频URL的数组赋值给它。

function displayVideos() {
    var container = document.getElementById("video-container");

    videoUrls.forEach(function(url) {
        var videoId = extractVideoId(url);

        var iframe = document.createElement("iframe");
        iframe.width = "560";
        iframe.height = "315";
        iframe.src = "https://www.youtube.com/embed/" + videoId;
        iframe.frameborder = "0";
        iframe.allowfullscreen = true;

        container.appendChild(iframe);
    });
}

定义一个名为`displayVideos`的函数。该函数将在`video-container`中显示视频。它遍历`videoUrls`数组中的每个URL，提取视频ID，并创建一个`iframe`元素来嵌入YouTube视频。

function extractVideoId(url) {
    var videoId = "";
    var regExp = /^.*((youtu.be\/)|(v\/)|(\/u\/\w\/)|(embed\/)|(watch\?))\??v?=?([^#&?]*).*/;

    var match = url.match(regExp);
    if (match && match[7].length === 11) {
        videoId = match[7];
    }

    return videoId;
}
定义一个名为extractVideoId`的函数，用于从YouTube视频URL中提取视频ID。它使用正则表达式来匹配不同类型的YouTube URL，并返回匹配到的视频ID。
window.onload = displayVideos;
在窗口加载完成后，调用`displayVideos`函数来显示视频。
</script>
JavaScript代码的结束标签。
</body>
HTML文档主体部分的结束标签。
</html>
HTML文档的结束标签。
