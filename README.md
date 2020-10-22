# 网站所需数据文件及其说明
- [calendar](#calendar)
-  [plenary_sessions](#plenary_sessions)
- [papers](#papers)
- [paper_zoom_links](#paper_zoom_links)
- [paper_slideslive_ids](#paper_slideslive_ids)
- [papers_projection](#papers_projection)
- [tutorials](#tutorials)
- [workshops_main_page](#workshops_main_page)
- [workshops_papers](#workshops_papers)
- [workshop_schedules](#workshops_papers)

# <span id = "calendar">calendar</span>
日程安排，对应[schedule](http://47.242.94.77:9090/schedule.html)页面。<br>
数据示例如下：
> calendar.josn 文件 <br>
>```
[
  {
    "title": "Tutorials",
    "start": "2020-07-05T13:00:00+00:00",
    "end": "2020-07-05T16:30:00+00:00",
    "location": "tutorials.html",
    "link": "tutorials.html",
    "category": "time",
    "calendarId": "---",
    "type": "Tutorials",
    "view": "week"
  },...]
### 数据类型说明

<table border="1">
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td>view</td>
        <td>显示模式，按天还是按周</td>
        <td>['week', 'day']</td>
    </tr>
    <tr>
        <td>title</td>
        <td>日程标题</td>
        <td>view=='week': title=type<br>
        view=='day':自定义的标题
        </td>
    </tr>    
    <tr>
        <td>type</td>
        <td>日程类型</td>
        <td>["Plenary Sessions", "Tutorials", "Workshops", "QA Sessions"]</td>
    </tr>
        <tr>
        <td>location</td>
        <td>该日程所在路由地址</td>
        <td>
            if view == 'week':
             {<br>
            type=='Plenary Sessions':plenary_session*.html;<br>
            type=='Tutorials':tutorials.html;<br>
            type=='Workshops':workshops.html;<br>
            type=='QA Session':papers.html?session=1A;<br>
            }<br>
            if view == 'day':{<br>
            type=='Plenary Sessions':plenary_session*.html;<br>
            type=='Tutorials':tutorial_T1.html;<br>
            type=='Workshops':workshop_W1.html;<br>
            type=='QA Session':papers.html?session=1A;<br>
            }
        </td>
    </tr>
        <tr>
        <td>link</td>
        <td>路由地址</td>
        <td>同location</td>
    </tr>
        <tr>
        <td>start</td>
        <td>开始日期</td>
        <td>参照"2020-07-05T13:00:00+00:00"</td>
    </tr>
            <tr>
        <td>start</td>
        <td>结束日期</td>
        <td>参照"2020-07-05T16:30:00+00:00"</td>
    </tr>
        <tr>
        <td>category</td>
        <td>分类</td>
        <td>默认 "time"</td>
    </tr>
            <tr>
        <td>calendarId</td>
        <td>日程ID</td>
        <td>默认 "---"</td>
    </tr>
</table>




# <span id = "plenary_sessions">plenary_sessions</span>
[全体会议](http://47.242.94.77:9090/plenary_sessions.html#tab-july6)
不确定用不用得上
数据示例如下：
> plenary_sessions.yml<br>
>
```
- UID: "opening_remarks"
  title: "Opening Remarks"
  image: static/images/acl2020/acl-logo.png
  date: July 6
  day: Monday
  sessions:
    - name: P-Live Presentation
      start_time: 2020-07-06_14:00:00
      end_time: 2020-07-06_14:15:00
  presenter: Dan Jurafsky, Joyce Chai, Natalie Schluter, Joel Tetreault
  youtube_id: Sx6dAx7dnXg
  bilibili_id:BV1kt4y1v7T6
  ```
 ### 数据类型说明
 <table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td>UID</td>
        <td>plenary sessions的ID，同title</td>
        <td>如，opening_remarks</td>
    </tr>
    <tr>
        <td>title</td>
        <td>plenary sessions的title</td>
        <td>如，opening_remarks</td>
    </tr>
        <tr>
        <td>image</td>
        <td>所展示图片</td>
        <td>默认为，static/images/acl2020/acl-logo.png</td>
    </tr>
        <tr>
        <td>sessions</td>
        <td>包含name, start_time, end_time</td>
        <td></td>
    </tr>
        <tr>
        <td>presenter</td>
        <td>作者</td>
        <td>如，Dan Jurafsky, Joyce Chai, Natalie Schluter, Joel Tetreault</td>
    </tr>
        <tr>
        <td>youtube_id</td>
        <td>youtube视频id</td>
        <td>如，Sx6dAx7dnXg</td>
    </tr>
        <tr>
        <td>bilibili_id</td>
        <td>bilibili视频BV id</td>
        <td>如，BV1kt4y1v7T6</td>
    </tr>
    
</table>


# <span id = "papers">papers</span>
papers分为五种类型，分别为[main_papers, demo_papers, srw_papers, cl_papers, tacl_papers]，每个类型对应一个csv文件，此处以demo_paper为例说明，其他类型具体参照文件。
> demo_papers.csv<br>
`UID,title,authors,abstract,keywords,track,paper_type,pdf_url,demo_url
demo.94,标题,作者1|作者2, 摘要,GAIA|Fine-grained System|open system|indexing entities,Demo,Demo,
https://www.aclweb.org/anthology/2020.acl-demos.11.pdf,https://blender.cs.illinois.edu/software/gaia-ie`

 <table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td>UID</td>
        <td>论文的id</td>
        <td>不同类别的论文id分别以其类别为开头<br>
        [main.1, demo.1, srw.1, cl.1, tacl.1]</td>
    </tr>
    <tr>
        <td>title</td>
        <td>论文标题</td>
        <td>论文标题</td>
    </tr>
        <tr>
        <td>authors</td>
        <td>作者</td>
        <td>以"|"分隔，如，zumi Haruta|Koji Mineshima|Daisuke Bekki</td>
    </tr>
        <tr>
        <td>abstract</td>
        <td>摘要</td>
        <td>需要加双引号，如"Comparative constructions pose a challenge"</td>
    </tr>
        <tr>
        <td>keywords</td>
        <td>关键词</td>
        <td>以"|"分隔，如，GAIA|Fine-grained System|open system|indexing entities</td>
    </tr>
        <tr>
        <td>track</td>
        <td></td>
        <td>同论文类型</td>
    </tr>
            <tr>
        <td>paper_type</td>
        <td>论文类型</td>
        <td>main 论文分[Long, Short]，其余类型根据其类名，分[Demo, Srw, Cl, Tacl]</td>
    </tr>
    <tr>
        <td>pdf_url</td>
        <td>论文的PDF下载链接</td>
        <td>如，https://www.aclweb.org/anthology/2020.acl-demos.11.pdf</td>
    </tr>
    <tr>
        <td>demo_url</td>
        <td>demo地址</td>
        <td>如github，https://allenai.github.io/spike </td>
    </tr>
</table>

# <span id = "paper_zoom_links">paper_zoom_links</span>
zoom会议地址，同样分为五种
> demo_paper_zoom_links.csv<br>
`UID,session_name,starttime,endtime,timezone,zoom_join_link
demo.24,D3A-1,2020-07-06T12:00:00Z,2020-07-06T12:45:00Z,UTC,https://zoom.us/j/93300035806`

<table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>UID</b></td>
        <td>论文的id</td>
        <td>同papers的ID，用于与其合并<br>
        [main.1, demo.1, srw.1, cl.1, tacl.1]</td>
    </tr>
    <tr>
        <td>session_name</td>
        <td>session name</td>
        <td>待定，如，D3A-1</td>
    </tr>
        <tr>
        <td>starttime</td>
        <td>开始时间</td>
        <td>2020-07-06T12:00:00Z</td>
    </tr>
        <tr>
        <td>endtime</td>
        <td>结束时间</td>
        <td>2020-07-06T12:45:00Z</td>
    </tr>
        <tr>
        <td>timezone</td>
        <td>时区</td>
        <td>默认，UTC</td>
    </tr>
        <tr>
        <td>zoom_join_link</td>
        <td>会议链接</td>
        <td>https://zoom.us/j/93300035806</td>
    </tr>
        
</table>


# <span id = "paper_slideslive_ids">paper_slideslive_ids</span>
同样是分为5种。因为我们不用slideslive，所以改为youtube和B站的视频ID
> paper_slideslive_ids.csv<br>
`UID,youtube_id, bilibili_id
main.1,Sx6dAx7dnXg, BV1kt4y1v7T6`
<table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>UID</b></td>
        <td>论文的id</td>
        <td>同papers的ID，用于与其合并<br>
        [main.1, demo.1, srw.1, cl.1, tacl.1]</td>
    </tr>
    <tr>
        <td>youtube_id</td>
        <td>youtube 视频id</td>
        <td>如，Sx6dAx7dnXg</td>
    </tr>
    <tr>
        <td>bilibili_id</td>
        <td>bilibili 视频id</td>
        <td>如，BV1kt4y1v7T6</td>
    </tr>
</table>

# <span id = "papers_projection">papers_projection</span>
保存论文相似度的坐标
> papers_projection.json<br>
>`[{"id": "main.1", "pos": [13.263115882873535, 7.318037509918213]},`

<table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>id</b></td>
        <td>论文的id</td>
        <td>同papers的ID，用于与其合并<br>
        [main.1, demo.1, srw.1, cl.1, tacl.1]</td>
    </tr>
    <tr>
        <td>pos</td>
        <td>论文相似度在坐标轴上的x,y坐标</td>
        <td>如，[13.263115882873535, 7.318037509918213]</td>
    </tr>

</table>

# <span id = "tutorials">tutorials</span>
[tutorials](http://47.242.94.77:9090/tutorials.html)
> tutorials.yml
```
- UID: T1
  title: Interpretability and Analysis in Neural NLP
  organizers: "Yonatan Belinkov, Sebastian Gehrmann and Ellie Pavlick"
  abstract: |
    While deep learning has transformed the natural language processing (NLP) field and impacted the larger
    computational linguistics community, the rise of neural networks is stained by their opaque nature: It is
    challenging to interpret the inner workings of neural network models, and explicate their behavior. Therefore, in
    the last few years, an increasingly large body of work has been devoted to the analysis and interpretation of
    neural network models in NLP. This body of work is so far lacking a common framework and methodology. Moreover,
    approaching the analysis of modern neural networks can be difficult for newcomers to the field. This tutorial aims
    to fill this gap and introduce the nascent field of interpretability and analysis of neural networks in NLP. The
    tutorial will cover the main lines of analysis work, such as structural analyses using probing classifiers,
    behavioral studies and test suites, and interactive visualizations. We will highlight not only the most commonly
    applied analysis methods, but also the specific limitations and shortcomings of current approaches, in order to
    inform participants where to focus future efforts.
  prerecorded: 38928626
  # rocketchat_channel: tutorial-1
  sessions:
    - name: Live Session 1
      start_time: 2020-07-05_13:00:00
      end_time: 2020-07-05_16:30:00
      livestream_id: 38931660
      # zoom_link: https://zoom.us/j/92074495706?pwd=NWNrTkxFWWpKc0JvcWNvUjVyZGhBZz09
    - name: Live Session 2
      start_time: 2020-07-05_17:30:00
      end_time: 2020-07-05_21:00:00
      livestream_id: 38931661
      zoom_link: https://zoom.us/j/92074495706?pwd=NWNrTkxFWWpKc0JvcWNvUjVyZGhBZz09
  info: |
    This tutorial has a prerecorded talk on this page (see below) that you can watch anytime during the conference. It
    also has two live sessions that will be conducted on Zoom and will be livestreamed on this page. Additionally, it has
    a chat window that you can use to have discussions with the tutorial teachers and other attendees anytime during the
    conference.
  website: ""
  material: ""
  slides: ""
```

<table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>UID</b></td>
        <td>tutorials的id</td>
        <td>以T开头，如，T1</td>
    </tr>
    <tr>
        <td>title</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>organizers</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>prerecorded</td>
        <td>相关视频，此处我们用youtube和bilibili的视频号代替</td>
        <td></td>
    </tr>
    <tr>
        <td>sessions</td>
        <td>sessions包含多个内容</td>
        <td></td>
    </tr>
    <tr>
        <td>info</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>website</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>material</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>slides</td>
        <td></td>
        <td></td>
    </tr>
</table>


# workshops
# <span id = "workshops_main_page">workshops_main_page</span>
[workshops demo website](http://47.242.94.77:9090/workshops.html)
> workshops.yml
```
- abstract: >
    The Fourth Widening NLP Workshop focuses on efforts to promote and support
    ideas and voices of underrepresented groups in Natural Language Processing. The
    2020 iteration of the workshop will, in particular, seek to highlight diversity
    in scientific background, discipline, training, obtained degrees, and seniority.
  day: 'July 5'
  livestream: 38931669
  website: http://www.winlp.org/winlp-2020-workshop/
  organizers:
    - Rossana Cunha
    - Samira Shaikh
    - Erika Varis
    - Ryan Georgi
    - Antonios Anastasopoulos
    - Khyathi Raghavi Chandu
    - Alicia Tsai
  rocketchat_channel: workshop-1-winlp
  sessions:
    - name: W-Live Session
      start_time: 2020-07-05_16:00:00
      end_time: 2020-07-05_23:00:00
      # zoom_link: https://zoom.us/j/94127596366?pwd=WDIwWjY3ZmgxbGdPbXVKZm5hNUNlZz09
  title: 'W1: WiNLP 2020 Workshop'
  UID: W1
```

<table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>UID</b></td>
        <td>workshop的id</td>
        <td>以W开头，如，W1</td>
    </tr>
    <tr>
        <td>abstract</td>
        <td>摘要</td>
        <td></td>
    </tr>
    <tr>
        <td>day</td>
        <td>日期</td>
        <td>需加单引号如，'July 5'</td>
    </tr>
    <tr>
        <td>livestream</td>
        <td>直播id，应该被取消了</td>
        <td></td>
    </tr>
    <tr>
        <td>organizers</td>
        <td>组织者</td>
        <td>包含多个</td>
    </tr>
    <tr>
        <td>sessions</td>
        <td>参考示例</td>
        <td></td>
    </tr>
    <tr>
        <td>zoom_link</td>
        <td>zoom链接</td>
        <td></td>
    </tr>
    <tr>
        <td>title</td>
        <td>标题</td>
        <td></td>
    </tr>

</table>

# <span id = " workshops_papers">workshops_papers</span>
具体的每个workshop中分享的[paper列表](http://47.242.94.77:9090/workshop_W1.html)<br>
有多个文件，w1-wn。
> w1_papers.csv<br>
>`UID,title,speakers,presentation_id
1,Corpus based Amharic sentiment lexicon generation,"Girma Neshir Alemneh, Andreas Rauber and Solomon Atnafu",38929537`

<table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>UID</b></td>
        <td>论文的id</td>
        <td>同papers的ID，用于与其合并<br>
        [main.1, demo.1, srw.1, cl.1, tacl.1]</td>
    </tr>
    <tr>
        <td>title</td>
        <td>标题</td>
        <td></td>
    </tr>
    <tr>
        <td>speakers</td>
        <td>演讲者</td>
        <td></td>
    </tr>
    <tr>
        <td>presentation_id</td>
        <td>视频ID,此处我们用youtube和bilibili的视频号代替</td>
        <td></td>
    </tr>
</table>


# <span id = "workshop_schedules">workshop_schedules</span>
workshop 的日程信息<br>
以<b>W<i>n</i></b>为大列表
> workshop_schedules.json<br>
> `{
  "W1":
  [
      {
        "id": "W0100",
        "title": "Opening remarks",
        "speakers": "Rossana Cunha, Samira Shaikh, Erika Varis, Ryan Georgi, Antonios Anastasopoulos, Khyathi Raghavi Chandu and Alicia Tsai",
        "type": "",
        "date": "Jul 5",
        "startTime": "9:00 AM",
        "endTime": "9:10 AM",
        "subsession": "Session 1"
      },...],
      "W2":[...],
      }`
      
 <table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td><b>id</b></td>
        <td>workshop的id</td>
        <td>如，W0100</td>
    </tr>
    <tr>
        <td>title</td>
        <td>标题</td>
        <td></td>
    </tr>
    <tr>
        <td>speakers</td>
        <td>演讲者</td>
        <td></td>
    </tr>
    <tr>
        <td>type</td>
        <td>workshop类型</td>
        <td></td>
    </tr>
    <tr>
        <td>date</td>
        <td>日期</td>
        <td></td>
    </tr>
    <tr>
        <td>startTime</td>
        <td>演讲者</td>
        <td></td>
    </tr>
    <tr>
        <td>endTime</td>
        <td>workshop类型</td>
        <td></td>
    </tr>
    <tr>
        <td>subsession</td>
        <td>隶属 session</td>
        <td>如，Session 1</td>
    </tr>
</table>
