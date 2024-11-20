<p dir="ltr" style="text-align: left;"></p>
<p><span><span style=""><span></span></span></span></p>
<h5><strong style="font-size: 1.17188rem;"><u>Problem:</u></strong><br></h5>
<div>The winter has come, yet the radiators are not made to work and METU Ceng students are freezing. All department students want is to be able to study in the department laboratories and study-rooms for 7x24. However, they can't do it because of the freezing cold of the department at nights. When they ask&nbsp;the Energy Department of the University to work the radiators, they take the following answer:</div>
<div><span style="font-size: 0.9375rem;"><br></span></div>
<div class="editor-indent" style="margin-left: 30px;">
    <div><span style="font-size: 0.9375rem;">"</span></div>
    <div><span style="font-size: 0.9375rem;">Dear students,&nbsp;</span></div>
    <div><span style="font-size: 0.9375rem;">We lost the 'pipeline usage plan' that provides us to work the radiators economically at the university overall. By using that plan, it is possible to activate the furnace rooms of only the keypoint buildings and work the radiators of the other buildings via the pipelines connected to those keypoints. Nonetheless, without the plan, we have to either activate all the furnace rooms (the furnace room of each building), or deactivate all. Since our budget can not afford to apply the first choice, we apply the second choice. We hope to find the usage plan as soon as possible.</span></div>
    <div><span style="font-size: 0.9375rem;"><strong>"</strong></span></div>
</div>
<div><br></div>
<div>Upon this reply, the lovely and clever 3rd class Ceng students become volunteer to solve the problem since they do no want to freeze anymore. They ask the map of pipelines in the university and start to work on a new pipeline usage plan.&nbsp;</div>
<div><span style="font-size: 0.9375rem;"><strong><br></strong></span></div>
<div><b>&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;<img src="https://github.com/user-attachments/assets/90735db8-84a1-47e5-bcf4-8977818049d7" alt="freezing_students" width="893" height="464" class="img-fluid atto_image_button_text-bottom"></b></div>
<div><b><br></b></div>
<div><span style="font-size: 0.9375rem;"><strong><br></strong></span></div>
<div class="editor-indent" style="margin-left: 30px;">
    <div><span style="font-size: 0.9375rem;"><strong><span class="" style="color: rgb(51, 102, 255);"><span class="" style="color: rgb(255, 102, 51);">P</span><span class="" style="color: rgb(255, 102, 51);">ART-I</span></span></strong></span></div>
</div>
<div class="editor-indent" style="margin-left: 30px;">
    <div><span>You should find a solution such that radiators of each building could be managable and the resulting energy consumption should be in the minimum level.&nbsp;</span></div>
</div>
<div>
    <ul>
        <ul>
            <li>Radiators of a building become managable either via activation of the furnace room of that building or via a pipeline connecting it to another building whose radiators are managed (by its own furnace room or again via a pipeline connected to some other building, so on).</li>
            <li>Each building has its own furnace room.</li>
            <li>Amount of the energy consumption is defined differently for each managing method. That is, each pipeline providing the energy transfer between the departments have a different cost (results in a different amount of energy consumption). Also, for each building the cost of activating its own furnace room differs.</li>
            <li>Note that it is necessary to activate the furnace room of at least one building (this becomes the source), so the others can find the energy through the pipelines reaching them to the source somehow.</li>
            <li>There can be more than one pipeline connection between two buildings, or between the building itself and its furnace room.</li>
            <li>There may be more than one cheapest way to warm up the whole university. It is enough for you to find only one.&nbsp; &nbsp;</li>
        </ul>
    </ul>
</div>
<div class="editor-indent" style="margin-left: 30px;">
    <p><u><span><strong>Implementation:</strong></span></u></p>
</div>
<div>
    <ul>
        <ul>
            <li>Each pipeline is defined as below:</li>
        </ul>
    </ul>
</div>
<div class="editor-indent" style="margin-left: 30px;">
    <div class="editor-indent" style="margin-left: 30px;">
        <pre><strong style="">struct Pipeline {<br></strong><strong>&nbsp; &nbsp; int id;<br></strong><strong>&nbsp; &nbsp; int end1;<br></strong><strong>&nbsp; &nbsp; int end2;<br></strong><strong>&nbsp; &nbsp; int cost_of_consumption;<br></strong><strong style="">};</strong></pre>
    </div>
</div><span style="font-size: 0.9375rem;">
    <ul style="">
        <ul style="">
            <ul style="">
                <li style=""><span style="font-size: 0.9375rem;"><em>id</em></span><span style="font-size: 0.9375rem;"> is a unique integer representing the id of the pipeline.</span></li>
                <li style=""><span style="font-size: 0.9375rem;"><em>end1</em></span><span style="font-size: 0.9375rem;"> and </span><span style="font-size: 0.9375rem;"><em>end2</em></span><span style="font-size: 0.9375rem;"> represents the building ids connected via the pipeline. Each building also has a unique id. If </span><span style="font-size: 0.9375rem;"><em>end1=end2</em></span><span style="font-size: 0.9375rem;">, then it means the pipeline represents the connection between the building itself and its own furnace room.</span></li>
                <li style=""><span style="font-size: 0.9375rem;"><em>amount_of_consumption</em></span><span style="font-size: 0.9375rem;"> is the cost/amount of the consumption caused by the usage of that pipeline.</span></li>
            </ul>
        </ul>
    </ul>
</span>
<div>
    <div>
        <ul>
            <ul>
                <li>You will implement the following function for the solution:</li>
            </ul>
        </ul>
    </div>
</div>
<div class="editor-indent" style="margin-left: 30px;">
    <div class="editor-indent" style="margin-left: 30px;">
        <div>
            <pre><span><span style=""><span><strong>vector&lt;int&gt; plan_min_cost_pipeline_usage(vector&lt;Pipeline*&gt; pipelines, int num_of_buildings);</strong></span></span></span></pre>
        </div>
    </div>
</div><span style="font-size: 0.9375rem;">
    <ul style="">
        <ul style="">
            <ul>
                <li style=""><em style="font-style: italic; font-size: 0.9375rem;">vector&lt;Pipeline*&gt; pipelines </em><span style="font-size: 0.9375rem;">holds the pipeline map of the university. Each pipeline is uniquely given in this vector. (The uniqueness is satisfied by the pipelined ids, the other </span><span style="font-size: 0.9375rem;">Pipeline</span><span style="font-size: 0.9375rem;"> members may be the same.)</span></li>
                <li style=""><em style="font-style: italic; font-size: 0.9375rem;">int num_of_buildings</em><span style="font-size: 0.9375rem;"> is the total number of buildings located in the university.</span></li>
                <li style=""><span style="font-size: 0.9375rem;">The function returns the usage plan holding the ids of the pipelines providing to warm up each building with the minimum cost/amoun<em>t.</em></span></li>
            </ul>
        </ul>
    </ul>
</span>
<div class="editor-indent" style="margin-left: 30px;"><span style="font-size: 0.9375rem;">
        <p><em></em></p>
    </span></div><span style="font-size: 0.9375rem;">
    <ul style="">
        <ul>
            <li style="">The ordering of the ids in the returned vector is not important.</li>
        </ul>
    </ul>
</span>
<div><br></div>
<div class="editor-indent" style="margin-left: 30px;">
    <div>
        <div><strong><span class="" style="color: rgb(255, 102, 51);">PART-II</span></strong></div>
    </div>
    <div>
        <div>After you find a solution in the first part, the Energy Department informs you that the current pipeline map is missing. They say that there actually exists one more pipeline which has been forgotten to put into the map. They request you to update your solution by considering this pipeline. It is also possible the pipeline does not affect the current solution, yet you should check it too.</div>
    </div>
</div>
<div>
    <div><br></div>
</div>
<div class="editor-indent" style="margin-left: 30px;">
    <div>
        <div>
            <p><u><span><strong>Implementation:</strong></span></u></p>
        </div>
    </div>
</div>
<div>
    <div>
        <div>
            <ul>
                <ul>
                    <li><span style="font-size: 0.9375rem;">You will implement the following function for the solution:</span></li>
                </ul>
            </ul>
        </div>
    </div>
</div>
<div class="editor-indent" style="margin-left: 30px;">
    <div class="editor-indent" style="margin-left: 30px;">
        <div>
            <div>
                <pre><strong>vector&lt;int&gt; optimize_plan(vector&lt;Pipeline*&gt; current_solution, Pipeline* new_pipeline);</strong></pre>
            </div>
        </div>
    </div>
</div>
<div class="editor-indent" style="margin-left: 30px;"></div>
<ul>
    <ul>
        <ul>
            <li><span style="font-size: 0.9375rem;"><em>vector&lt;Pipeline*&gt; current_solution</em> is the solution that is expected to be found in the PART-I, yet the vector holds the pipelines itselves, not their ids.. We will call the method by supplying this solution in the first argument.</span></li>
            <li><span style="font-size: 0.9375rem;"><em>Pipeline* new_pipeline</em> is the new pipeline which is missing in the previous map.</span></li>
            <li><span style="font-size: 0.9375rem;">The function returns the updated usage plan holding the ids of the pipelines.</span></li>
        </ul>
    </ul>
</ul>
<div>
    <div><span style="">
            <ul>
                <ul>
                    <li>The ordering of the ids in the returned vector is not important.</li>
                    <li><strong>You are required to implement a <em>O(N)</em> solution where <em>N </em>is the number of buildings. This requirement consists of 20% of THE in grading.</strong></li>
                    <li><span>Note that it would be enough to hold an efficient data structure like <strong>adjacency matrix of the graph</strong>. There is no need to use complex structures like heap etc.</span></li>
                </ul>
            </ul>
        </span></div>
</div>
<h5><strong><u>Example IO:</u></strong></h5>
<div class="editor-indent" style="margin-left: 30px;">
    <div><span style="font-size: 0.9375rem;"><strong><span class="" style="color: rgb(255, 102, 51);">Example-1:</span></strong></span></div>
</div>
<div><span style="font-size: 0.9375rem;">
        <p></p>
    </span><span style="font-size: 0.9375rem;"></span></div>
<div><span style="font-size: 0.9375rem;"><strong><img src="https://github.com/user-attachments/assets/4e7c61dd-19f0-4b41-b985-5c339598d77c" alt="example1" width="1171" height="731" class="img-fluid atto_image_button_text-bottom"><br></strong></span></div>
<div class="editor-indent" style="margin-left: 30px;"><strong><span class="" style="color: rgb(255, 102, 51);">Example-2:</span></strong></div><img src="https://github.com/user-attachments/assets/6770324e-9bc4-4a9c-b50e-03663c9f982b" alt="example2" width="1056" height="691" class="img-fluid atto_image_button_text-bottom"><br>
<div class="editor-indent" style="margin-left: 30px;"><strong><span class="" style="color: rgb(255, 102, 51);">Example-3:</span></strong></div><img src="https://github.com/user-attachments/assets/f4724ced-ca6c-4464-aaac-883624d911da" alt="example3_input" width="1464" height="738" class="img-fluid atto_image_button_text-bottom"><br><img src="https://github.com/user-attachments/assets/adce3dfd-75cd-4d3b-80e4-3e1af7661014" alt="example3_output" width="1414" height="717" class="img-fluid atto_image_button_text-bottom"><br>
<div class="editor-indent" style="margin-left: 30px;"><strong><span class="" style="color: rgb(255, 102, 51);">Example-4:</span></strong></div><img src="https://github.com/user-attachments/assets/ac4cad07-07dc-49d8-ba7c-65043bea0898" alt="example4" width="1326" height="739" class="img-fluid atto_image_button_text-bottom"><br><br>
<h5><span><strong><u>Constraints:</u></strong></span></h5><span>
    <ul style="">
        <li style=""><span style="font-size: 0.9375rem;">Maximum number of buildings in the university will be&nbsp;</span><span style="font-size: 0.9375rem;">512</span><span style="font-size: 0.9375rem;">.&nbsp;</span></li>
        <li style=""><span style="font-size: 0.9375rem;">Maximum number of pipelines is 4096.</span></li>
        <li style=""><span style="font-size: 0.9375rem;">Only for the Testcase-11, this limits change. Maximum&nbsp; number of buildings for this testcase is 2<sup>18</sup>.</span></li>
    </ul>
</span>
<h5><strong><u>Evaluation:</u></strong></h5>
<p></p>
<ul>
    <li>After your exam, black box evaluation will be carried out. You will get full points if your both function returns the correct result without exceeding time limit.</li>
    <li>There are 10 testcases to test output of the functions.&nbsp;PART-I is 7 points and PART-II is 1 points for each.</li>
    <li>There is one last testcase (Testcase-11) which checks the complexity of your implementation for PART-II. This testcase will be run only if you get full credit for Part-II implementation from all other testcases. If your Part-II implementation is O(N) (where N is the number of buildings), then you get 20 points. If it is more, then you get 0.</li>
    <li>The grading of PART-I and PART-II are independent from each other. Only the Testcase-11 is dependent to get full credit from PART-II for each testcase.</li>
</ul><br>
<h5><u><strong>Specifications:</strong></u></h5>
<ul>
    <li>There are&nbsp;<strong>only</strong><strong><strong>&nbsp;2 tasks</strong></strong>&nbsp;to be solved in&nbsp;<strong>12 hours</strong>&nbsp;in this take home exam.</li>
    <li>You will implement your solutions in&nbsp;<strong>the6.cpp</strong>&nbsp;file.</li>
    <li>Do&nbsp;<strong>not&nbsp;</strong>change the first line of&nbsp;<strong>the6.cpp</strong>, which is&nbsp;<strong>#include "the6.h"</strong></li>
    <li><em>&lt;iostream&gt;,&nbsp; &lt;climits&gt;,</em><em>&nbsp;&lt;vector&gt;, &lt;string&gt;, &lt;stack&gt;, &lt;queue&gt;,&nbsp;<em>&lt;unordered_set&gt;</em> </em>are included in "the6.h" for your convenience.</li>
    <li>Do&nbsp;<strong>not&nbsp;</strong>change the arguments and return&nbsp;<strong>types</strong>&nbsp;of the functions<strong>.</strong><strong>&nbsp;</strong>(You should change return&nbsp;<strong>value</strong>, on the other hand.)<strong><br></strong></li>
    <li>Do&nbsp;<strong>not&nbsp;</strong>include any other library or write include anywhere in your&nbsp;<strong>the6.cpp</strong>&nbsp;file (not even in comments)</li>
</ul>
<h5><strong><u>Compilation:</u></strong></h5>
<p></p>
<ul>
    <li>You are given&nbsp;<strong>test.cpp</strong>&nbsp;file to&nbsp;<strong>test&nbsp;</strong>your work on&nbsp;<strong>ODTÜClass</strong>&nbsp;or your&nbsp;<strong>locale</strong>. You can and you are encouraged to modify this file to add different test cases.</li>
    <li>If you want to&nbsp;<strong>test&nbsp;</strong>your work and see your outputs you can&nbsp;<strong>compile and run&nbsp;</strong>your work on your locale as:</li>
</ul>
<table cellspacing="0" cellpadding="0" border="1">
    <tbody>
        <tr>
            <td width="604" valign="top">
                <p>&gt;g++ test.cpp the6.cpp -Wall -std=c++11 -o test</p>
                <p>&gt; ./test</p>
            </td>
        </tr>
    </tbody>
</table><br>
<ul>
    <li>You can test your&nbsp;<strong>the6.cpp</strong>&nbsp;on virtual lab environment. If you click&nbsp;<strong>run</strong>, your function will be compiled and executed with&nbsp;<strong>test.cpp</strong>. If you click&nbsp;<strong>evaluate</strong>, you will get a feedback for your current work and your work will be&nbsp;<strong>temporarily&nbsp;</strong>graded for&nbsp;<strong>limited&nbsp;</strong>number of inputs.</li>
    <li>The grade you see in lab is&nbsp;<strong>not</strong>&nbsp;your final grade, your code will be re-evaluated with&nbsp;<strong>completely</strong>&nbsp;<strong>different&nbsp;</strong>inputs after the exam.</li>
</ul>
<p>The system has the following limits:</p>
<ul>
    <li>a maximum execution time of 32 seconds for the Testcases 1-10, and 60 seconds for the Testcase11</li>
    <li>a 4GiB maximum memory limit</li>
    <li>an execution file size of 128MiB</li>
    <li>If you are sure that your solution works in the expected complexity constrains but your evaluation fails due to limits in the lab environment, the constant factors may be the problem.<br><br></li>
</ul>
<table width="656" cellspacing="0" cellpadding="0" border="1">
    <tbody>
        <tr>
            <td width="656" valign="top">
                <p>vector&lt;int&gt; plan_min_cost_pipeline_usage(vector&lt;Pipeline*&gt; pipelines, int num_of_buildings);</p>
                <p>vector&lt;int&gt; optimize_plan(vector&lt;Pipeline*&gt; current_solution, Pipeline* new_pipeline);</p>
            </td>
        </tr>
    </tbody>
</table>
<div><br></div><br>&nbsp; <img src="https://github.com/user-attachments/assets/70076d34-fcc4-4d17-a42b-804c0a5e2a96" alt="bugsbunny" width="300" height="250" class="atto_image_button_text-bottom"><br>
<p></p>
