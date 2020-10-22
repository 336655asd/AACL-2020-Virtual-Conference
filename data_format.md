 ### 数据类型说明
 <table>
    <th>列名</th>
    <th>说明</th>
    <th>取值</th>
    <tr>
        <td>type</td>
        <td>项目类型，[paper, session, event]三种之一</td>
        <td>如，paper</td>
    </tr>
    <tr>
        <td>title</td>
        <td>标题</td>
        <td>如，Touch Editing: A Flexible One-Time Interaction Approach for Translation</td>
    </tr>
    <tr>
        <td>abstract</td>
        <td>paper摘要，如非paper默认为 "none"</td>
        <td>如，We propose a touch-based editing method for translation, <br>
            which is more ﬂexible than traditional keyboard-mouse-based translation postediting. </td>
    </tr>
        <tr>
        <td>authors</td>
        <td>作者，如非paper默认为 "none"</td>
        <td>如，Qian Wang|Jiajun Zhang|Lemao Liu|Guoping Huang|Chengqing Zong</td>
    </tr>
        <tr>
        <td>org</td>
        <td>作者所在机构，如非paper默认为 "none"</td>
        <td>Institute of Automation|Chinese Academy of Sciences|Institute of Automation Chinese Academy of Sciences|Tencent AI Lab</td>
    </tr>
         <tr>
        <td>paper_id</td>
        <td>paper id，为对应html前缀数字，如非paper默认为 "none"</td>
        <td>如，39</td>
    </tr>
        <tr>
        <td>session</td>
        <td>session名，如非paper默认为 "none"</td>
        <td>如，Session 1A</td>
    </tr>
        <tr>
        <td>start</td>
        <td>开始时间</td>
        <td>如，2020-07-05T13:00:00+00:00</td>
    </tr>
        <tr>
        <td>end</td>
        <td>结束时间</td>
        <td>如，2020-07-05T14:00:00+00:00</td>
    </tr>
    
</table>

> 数据以JSON格式保存，示例如下

```
[
{"type": "event",
"title": "Opening Remarks",
"abstract": "none",
"authors": "none",
"org": "none",
"paper_id": "none",
"session": "none",
"start": "2020-12-05T08:45+00:00",
"end": "2020-12-05T09:00+00:00"
},
{"type": "session",
"title": "Machine Translation and Multilinguality I",
"abstract": "none",
"paper_id": "none",
"authors": "none",
"org": "none",
"session": "1A",
"start": "2020-12-05T10:00+00:00",
"end": "2020-12-05T11:00+00:00"
},
{"type": "paper",
"title": "Touch Editing: A Flexible One-Time Interaction Approach for Translation",
"abstract": "We propose a touch-based editing method for translation, which is more ﬂexible than traditional keyboard-mouse-based translation postediting. This approach relies on touch actions that users perform to indicate translation errors. We present a dual-encoder model to handle the actions and generate reﬁned translations. To mimic the user feedback, we adopt the TER algorithm comparing between draft translations and references to automatically extract the simulated actions for training data construction. Experiments on translation datasets with simulated editing actions show that our method significantly improves original translation of Transformer (up to 25.31 BLEU) and outperforms existing interactive translation methods (up to 16.64 BLEU). We also conduct experiments on post-editing dataset to further prove the robustness and effectiveness of our method.",
"authors": "Qian Wang|Jiajun Zhang|Lemao Liu|Guoping Huang|Chengqing Zong",
"org": "nstitute of Automation|Chinese Academy of Sciences|Institute of Automation Chinese Academy of Sciences|Tencent AI Lab",
"paper_id": 39,
"session": "1A",
"start": "2020-12-05T10:00+00:00",
"end": "2020-12-05T10:20+00:00"
},...
]

```
