---


---

<hr>
<p>title: Bash scripting<br>
keywords:</p>
<ul>
<li>Variables</li>
<li>Functions</li>
<li>Interpolation</li>
<li>Brace expansions</li>
<li>Loops</li>
<li>Conditional execution</li>
<li>Command substitution</li>
</ul>
<hr>
<h2 id="getting-started">Getting started</h2>
<p>{: .-three-column}</p>
<h3 id="introduction">Introduction</h3>
<p>{: .-intro}</p>
<p>This is a quick reference to getting started with Bash scripting.</p>
<ul>
<li><a href="https://learnxinyminutes.com/docs/bash/">Learn bash in y minutes</a> <em>(<a href="http://learnxinyminutes.com">learnxinyminutes.com</a>)</em></li>
<li><a href="http://mywiki.wooledge.org/BashGuide">Bash Guide</a> <em>(<a href="http://mywiki.wooledge.org">mywiki.wooledge.org</a>)</em></li>
</ul>
<h3 id="example">Example</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment">#!/usr/bin/env bash</span>

NAME<span class="token operator">=</span><span class="token string">"John"</span>
<span class="token keyword">echo</span> <span class="token string">"Hello <span class="token variable">$NAME!</span>"</span>
</code></pre>
<h3 id="variables">Variables</h3>
<pre class=" language-bash"><code class="prism  language-bash">NAME<span class="token operator">=</span><span class="token string">"John"</span>
<span class="token keyword">echo</span> <span class="token variable">$NAME</span>
<span class="token keyword">echo</span> <span class="token string">"<span class="token variable">$NAME</span>"</span>
<span class="token keyword">echo</span> <span class="token string">"<span class="token variable">${NAME}</span>!"</span>
</code></pre>
<h3 id="string-quotes">String quotes</h3>
<pre class=" language-bash"><code class="prism  language-bash">NAME<span class="token operator">=</span><span class="token string">"John"</span>
<span class="token keyword">echo</span> <span class="token string">"Hi <span class="token variable">$NAME</span>"</span>  <span class="token comment">#=&gt; Hi John</span>
<span class="token keyword">echo</span> <span class="token string">'Hi <span class="token variable">$NAME</span>'</span>  <span class="token comment">#=&gt; Hi $NAME</span>
</code></pre>
<h3 id="shell-execution">Shell execution</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> <span class="token string">"I'm in <span class="token variable"><span class="token variable">$(</span><span class="token function">pwd</span><span class="token variable">)</span></span>"</span>
<span class="token keyword">echo</span> <span class="token string">"I'm in <span class="token variable"><span class="token variable">`</span><span class="token function">pwd</span><span class="token variable">`</span></span>"</span>
<span class="token comment"># Same</span>
</code></pre>
<p>See <a href="http://wiki.bash-hackers.org/syntax/expansion/cmdsubst">Command substitution</a></p>
<h3 id="conditional-execution">Conditional execution</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">git</span> commit <span class="token operator">&amp;&amp;</span> <span class="token function">git</span> push
<span class="token function">git</span> commit <span class="token operator">||</span> <span class="token keyword">echo</span> <span class="token string">"Commit failed"</span>
</code></pre>
<h3 id="functions">Functions</h3>
<p>{: id=‘functions-example’}</p>
<pre class=" language-bash"><code class="prism  language-bash">get_name<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">echo</span> <span class="token string">"John"</span>
<span class="token punctuation">}</span>

<span class="token keyword">echo</span> <span class="token string">"You are <span class="token variable"><span class="token variable">$(</span>get_name<span class="token variable">)</span></span>"</span>
</code></pre>
<p>See: <a href="#functions">Functions</a></p>
<h3 id="conditionals">Conditionals</h3>
<p>{: id=‘conditionals-example’}</p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> -z <span class="token string">"<span class="token variable">$string</span>"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"String is empty"</span>
<span class="token keyword">elif</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> -n <span class="token string">"<span class="token variable">$string</span>"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"String is not empty"</span>
<span class="token keyword">fi</span>
</code></pre>
<p>See: <a href="#conditionals">Conditionals</a></p>
<h3 id="strict-mode">Strict mode</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">set</span> -euo pipefail
IFS<span class="token operator">=</span>$<span class="token string">'\n\t'</span>
</code></pre>
<p>See: <a href="http://redsymbol.net/articles/unofficial-bash-strict-mode/">Unofficial bash strict mode</a></p>
<h3 id="brace-expansion">Brace expansion</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> <span class="token punctuation">{</span>A,B<span class="token punctuation">}</span>.js
</code></pre>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>{A,B}</code></td>
<td>Same as <code>A B</code></td>
</tr>
<tr>
<td><code>{A,B}.js</code></td>
<td>Same as <code>A.js B.js</code></td>
</tr>
<tr>
<td><code>{1..5}</code></td>
<td>Same as <code>1 2 3 4 5</code></td>
</tr>
</tbody>
</table><p>See: <a href="http://wiki.bash-hackers.org/syntax/expansion/brace">Brace expansion</a></p>
<h2 id="parameter-expansions">Parameter expansions</h2>
<p>{: .-three-column}</p>
<h3 id="basics">Basics</h3>
<pre class=" language-bash"><code class="prism  language-bash">name<span class="token operator">=</span><span class="token string">"John"</span>
<span class="token keyword">echo</span> <span class="token variable">${name}</span>
<span class="token keyword">echo</span> <span class="token variable">${name/J/j}</span>    <span class="token comment">#=&gt; "john" (substitution)</span>
<span class="token keyword">echo</span> <span class="token variable">${name:0:2}</span>    <span class="token comment">#=&gt; "Jo" (slicing)</span>
<span class="token keyword">echo</span> <span class="token variable">${name::2}</span>     <span class="token comment">#=&gt; "Jo" (slicing)</span>
<span class="token keyword">echo</span> <span class="token variable">${name::-1}</span>    <span class="token comment">#=&gt; "Joh" (slicing)</span>
<span class="token keyword">echo</span> <span class="token variable">${name:(-1)}</span>   <span class="token comment">#=&gt; "n" (slicing from right)</span>
<span class="token keyword">echo</span> <span class="token variable">${name:(-2):1}</span> <span class="token comment">#=&gt; "h" (slicing from right)</span>
<span class="token keyword">echo</span> <span class="token variable">${food:-Cake}</span>  <span class="token comment">#=&gt; $food or "Cake"</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">length<span class="token operator">=</span>2
<span class="token keyword">echo</span> <span class="token variable">${name:0:length}</span>  <span class="token comment">#=&gt; "Jo"</span>
</code></pre>
<p>See: <a href="http://wiki.bash-hackers.org/syntax/pe">Parameter expansion</a></p>
<pre class=" language-bash"><code class="prism  language-bash">STR<span class="token operator">=</span><span class="token string">"/path/to/foo.cpp"</span>
<span class="token keyword">echo</span> <span class="token variable">${STR%.cpp}</span>    <span class="token comment"># /path/to/foo</span>
<span class="token keyword">echo</span> <span class="token variable">${STR%.cpp}</span>.o  <span class="token comment"># /path/to/foo.o</span>
<span class="token keyword">echo</span> <span class="token variable">${STR%/*}</span>      <span class="token comment"># /path/to</span>

<span class="token keyword">echo</span> $<span class="token punctuation">{</span>STR<span class="token comment">##*.}     # cpp (extension)</span>
<span class="token keyword">echo</span> $<span class="token punctuation">{</span>STR<span class="token comment">##*/}     # foo.cpp (basepath)</span>

<span class="token keyword">echo</span> $<span class="token punctuation">{</span>STR<span class="token comment">#*/}      # path/to/foo.cpp</span>
<span class="token keyword">echo</span> $<span class="token punctuation">{</span>STR<span class="token comment">##*/}     # foo.cpp</span>

<span class="token keyword">echo</span> <span class="token variable">${STR/foo/bar}</span> <span class="token comment"># /path/to/bar.cpp</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">STR<span class="token operator">=</span><span class="token string">"Hello world"</span>
<span class="token keyword">echo</span> <span class="token variable">${STR:6:5}</span>   <span class="token comment"># "world"</span>
<span class="token keyword">echo</span> <span class="token variable">${STR: -5:5}</span>  <span class="token comment"># "world"</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">SRC<span class="token operator">=</span><span class="token string">"/path/to/foo.cpp"</span>
BASE<span class="token operator">=</span>$<span class="token punctuation">{</span>SRC<span class="token comment">##*/}   #=&gt; "foo.cpp" (basepath)</span>
DIR<span class="token operator">=</span><span class="token variable">${SRC%$BASE}</span>  <span class="token comment">#=&gt; "/path/to/" (dirpath)</span>
</code></pre>
<h3 id="substitution">Substitution</h3>

<table>
<thead>
<tr>
<th>Code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>${FOO%suffix}</code></td>
<td>Remove suffix</td>
</tr>
<tr>
<td><code>${FOO#prefix}</code></td>
<td>Remove prefix</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>${FOO%%suffix}</code></td>
<td>Remove long suffix</td>
</tr>
<tr>
<td><code>${FOO##prefix}</code></td>
<td>Remove long prefix</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>${FOO/from/to}</code></td>
<td>Replace first match</td>
</tr>
<tr>
<td><code>${FOO//from/to}</code></td>
<td>Replace all</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>${FOO/%from/to}</code></td>
<td>Replace suffix</td>
</tr>
<tr>
<td><code>${FOO/#from/to}</code></td>
<td>Replace prefix</td>
</tr>
</tbody>
</table><h3 id="comments">Comments</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># Single line comment</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">:</span> <span class="token string">'
This is a
multi line
comment
'</span>
</code></pre>
<h3 id="substrings">Substrings</h3>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>${FOO:0:3}</code></td>
<td>Substring <em>(position, length)</em></td>
</tr>
<tr>
<td><code>${FOO:(-3):3}</code></td>
<td>Substring from the right</td>
</tr>
</tbody>
</table><h3 id="length">Length</h3>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>${#FOO}</code></td>
<td>Length of <code>$FOO</code></td>
</tr>
</tbody>
</table><h3 id="manipulation">Manipulation</h3>
<pre class=" language-bash"><code class="prism  language-bash">STR<span class="token operator">=</span><span class="token string">"HELLO WORLD!"</span>
<span class="token keyword">echo</span> <span class="token variable">${STR,}</span>   <span class="token comment">#=&gt; "hELLO WORLD!" (lowercase 1st letter)</span>
<span class="token keyword">echo</span> <span class="token variable">${STR,,}</span>  <span class="token comment">#=&gt; "hello world!" (all lowercase)</span>

STR<span class="token operator">=</span><span class="token string">"hello world!"</span>
<span class="token keyword">echo</span> <span class="token variable">${STR^}</span>   <span class="token comment">#=&gt; "Hello world!" (uppercase 1st letter)</span>
<span class="token keyword">echo</span> <span class="token variable">${STR^^}</span>  <span class="token comment">#=&gt; "HELLO WORLD!" (all uppercase)</span>
</code></pre>
<h3 id="default-values">Default values</h3>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>${FOO:-val}</code></td>
<td><code>$FOO</code>, or <code>val</code> if unset (or null)</td>
</tr>
<tr>
<td><code>${FOO:=val}</code></td>
<td>Set <code>$FOO</code> to <code>val</code> if unset (or null)</td>
</tr>
<tr>
<td><code>${FOO:+val}</code></td>
<td><code>val</code> if <code>$FOO</code> is set (and not null)</td>
</tr>
<tr>
<td><code>${FOO:?message}</code></td>
<td>Show error message and exit if <code>$FOO</code> is unset (or null)</td>
</tr>
</tbody>
</table><p>Omitting the <code>:</code> removes the (non)nullity checks, e.g. <code>${FOO-val}</code> expands to <code>val</code> if unset otherwise <code>$FOO</code>.</p>
<h2 id="loops">Loops</h2>
<p>{: .-three-column}</p>
<h3 id="basic-for-loop">Basic for loop</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> i <span class="token keyword">in</span> /etc/rc.*<span class="token punctuation">;</span> <span class="token keyword">do</span>
  <span class="token keyword">echo</span> <span class="token variable">$i</span>
<span class="token keyword">done</span>
</code></pre>
<h3 id="c-like-for-loop">C-like for loop</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> <span class="token variable"><span class="token punctuation">((</span>i <span class="token operator">=</span> <span class="token number">0</span> <span class="token punctuation">;</span> i <span class="token operator">&lt;</span> <span class="token number">100</span> <span class="token punctuation">;</span> i<span class="token operator">++</span><span class="token punctuation">))</span></span><span class="token punctuation">;</span> <span class="token keyword">do</span>
  <span class="token keyword">echo</span> <span class="token variable">$i</span>
<span class="token keyword">done</span>
</code></pre>
<h3 id="ranges">Ranges</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token punctuation">{</span>1<span class="token punctuation">..</span>5<span class="token punctuation">}</span><span class="token punctuation">;</span> <span class="token keyword">do</span>
    <span class="token keyword">echo</span> <span class="token string">"Welcome <span class="token variable">$i</span>"</span>
<span class="token keyword">done</span>
</code></pre>
<h4 id="with-step-size">With step size</h4>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token punctuation">{</span>5<span class="token punctuation">..</span>50<span class="token punctuation">..</span>5<span class="token punctuation">}</span><span class="token punctuation">;</span> <span class="token keyword">do</span>
    <span class="token keyword">echo</span> <span class="token string">"Welcome <span class="token variable">$i</span>"</span>
<span class="token keyword">done</span>
</code></pre>
<h3 id="reading-lines">Reading lines</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">cat</span> file.txt <span class="token operator">|</span> <span class="token keyword">while</span> <span class="token function">read</span> line<span class="token punctuation">;</span> <span class="token keyword">do</span>
  <span class="token keyword">echo</span> <span class="token variable">$line</span>
<span class="token keyword">done</span>
</code></pre>
<h3 id="forever">Forever</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">while</span> <span class="token boolean">true</span><span class="token punctuation">;</span> <span class="token keyword">do</span>
  ···
<span class="token keyword">done</span>
</code></pre>
<h2 id="functions-1">Functions</h2>
<p>{: .-three-column}</p>
<h3 id="defining-functions">Defining functions</h3>
<pre class=" language-bash"><code class="prism  language-bash">myfunc<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">echo</span> <span class="token string">"hello <span class="token variable">$1</span>"</span>
<span class="token punctuation">}</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># Same as above (alternate syntax)</span>
<span class="token keyword">function</span> myfunc<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">echo</span> <span class="token string">"hello <span class="token variable">$1</span>"</span>
<span class="token punctuation">}</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">myfunc <span class="token string">"John"</span>
</code></pre>
<h3 id="returning-values">Returning values</h3>
<pre class=" language-bash"><code class="prism  language-bash">myfunc<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    local myresult<span class="token operator">=</span><span class="token string">'some value'</span>
    <span class="token keyword">echo</span> <span class="token variable">$myresult</span>
<span class="token punctuation">}</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">result<span class="token operator">=</span><span class="token string">"<span class="token variable"><span class="token variable">$(</span>myfunc<span class="token variable">)</span></span>"</span>
</code></pre>
<h3 id="raising-errors">Raising errors</h3>
<pre class=" language-bash"><code class="prism  language-bash">myfunc<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">return</span> 1
<span class="token punctuation">}</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> myfunc<span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"success"</span>
<span class="token keyword">else</span>
  <span class="token keyword">echo</span> <span class="token string">"failure"</span>
<span class="token keyword">fi</span>
</code></pre>
<h3 id="arguments">Arguments</h3>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>$#</code></td>
<td>Number of arguments</td>
</tr>
<tr>
<td><code>$*</code></td>
<td>All arguments</td>
</tr>
<tr>
<td><code>$@</code></td>
<td>All arguments, starting from first</td>
</tr>
<tr>
<td><code>$1</code></td>
<td>First argument</td>
</tr>
<tr>
<td><code>$_</code></td>
<td>Last argument of the previous command</td>
</tr>
</tbody>
</table><p>See <a href="http://wiki.bash-hackers.org/syntax/shellvars#special_parameters_and_shell_variables">Special parameters</a>.</p>
<h2 id="conditionals-1">Conditionals</h2>
<p>{: .-three-column}</p>
<h3 id="conditions">Conditions</h3>
<p>Note that <code>[[</code> is actually a command/program that returns either <code>0</code> (true) or <code>1</code> (false). Any program that obeys the same logic (like all base utils, such as <code>grep(1)</code> or <code>ping(1)</code>) can be used as condition, see examples.</p>

<table>
<thead>
<tr>
<th>Condition</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>[[ -z STRING ]]</code></td>
<td>Empty string</td>
</tr>
<tr>
<td><code>[[ -n STRING ]]</code></td>
<td>Not empty string</td>
</tr>
<tr>
<td><code>[[ STRING == STRING ]]</code></td>
<td>Equal</td>
</tr>
<tr>
<td><code>[[ STRING != STRING ]]</code></td>
<td>Not Equal</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>[[ NUM -eq NUM ]]</code></td>
<td>Equal</td>
</tr>
<tr>
<td><code>[[ NUM -ne NUM ]]</code></td>
<td>Not equal</td>
</tr>
<tr>
<td><code>[[ NUM -lt NUM ]]</code></td>
<td>Less than</td>
</tr>
<tr>
<td><code>[[ NUM -le NUM ]]</code></td>
<td>Less than or equal</td>
</tr>
<tr>
<td><code>[[ NUM -gt NUM ]]</code></td>
<td>Greater than</td>
</tr>
<tr>
<td><code>[[ NUM -ge NUM ]]</code></td>
<td>Greater than or equal</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>[[ STRING =~ STRING ]]</code></td>
<td>Regexp</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>(( NUM &lt; NUM ))</code></td>
<td>Numeric conditions</td>
</tr>
</tbody>
</table><h4 id="more-conditions">More conditions</h4>

<table>
<thead>
<tr>
<th>Condition</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>[[ -o noclobber ]]</code></td>
<td>If OPTIONNAME is enabled</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>[[ ! EXPR ]]</code></td>
<td>Not</td>
</tr>
<tr>
<td><code>[[ X &amp;&amp; Y ]]</code></td>
<td>And</td>
</tr>
<tr>
<td><code>[[ X || Y ]]</code></td>
<td>Or</td>
</tr>
</tbody>
</table><h3 id="file-conditions">File conditions</h3>

<table>
<thead>
<tr>
<th>Condition</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>[[ -e FILE ]]</code></td>
<td>Exists</td>
</tr>
<tr>
<td><code>[[ -r FILE ]]</code></td>
<td>Readable</td>
</tr>
<tr>
<td><code>[[ -h FILE ]]</code></td>
<td>Symlink</td>
</tr>
<tr>
<td><code>[[ -d FILE ]]</code></td>
<td>Directory</td>
</tr>
<tr>
<td><code>[[ -w FILE ]]</code></td>
<td>Writable</td>
</tr>
<tr>
<td><code>[[ -s FILE ]]</code></td>
<td>Size is &gt; 0 bytes</td>
</tr>
<tr>
<td><code>[[ -f FILE ]]</code></td>
<td>File</td>
</tr>
<tr>
<td><code>[[ -x FILE ]]</code></td>
<td>Executable</td>
</tr>
<tr>
<td>—</td>
<td>—</td>
</tr>
<tr>
<td><code>[[ FILE1 -nt FILE2 ]]</code></td>
<td>1 is more recent than 2</td>
</tr>
<tr>
<td><code>[[ FILE1 -ot FILE2 ]]</code></td>
<td>2 is more recent than 1</td>
</tr>
<tr>
<td><code>[[ FILE1 -ef FILE2 ]]</code></td>
<td>Same files</td>
</tr>
</tbody>
</table><h3 id="example-1">Example</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># String</span>
<span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> -z <span class="token string">"<span class="token variable">$string</span>"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"String is empty"</span>
<span class="token keyword">elif</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> -n <span class="token string">"<span class="token variable">$string</span>"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"String is not empty"</span>
<span class="token keyword">else</span>
  <span class="token keyword">echo</span> <span class="token string">"This never happens"</span>
<span class="token keyword">fi</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># Combinations</span>
<span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> X <span class="token operator">&amp;&amp;</span> Y <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token punctuation">..</span>.
<span class="token keyword">fi</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># Equal</span>
<span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> <span class="token string">"<span class="token variable">$A</span>"</span> <span class="token operator">==</span> <span class="token string">"<span class="token variable">$B</span>"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token comment"># Regex</span>
<span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> <span class="token string">"A"</span> <span class="token operator">=</span>~ <span class="token keyword">.</span> <span class="token punctuation">]</span><span class="token punctuation">]</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> <span class="token variable"><span class="token punctuation">((</span> $a <span class="token operator">&lt;</span> $b <span class="token punctuation">))</span></span><span class="token punctuation">;</span> <span class="token keyword">then</span>
   <span class="token keyword">echo</span> <span class="token string">"<span class="token variable">$a</span> is smaller than <span class="token variable">$b</span>"</span>
<span class="token keyword">fi</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> -e <span class="token string">"file.txt"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"file exists"</span>
<span class="token keyword">fi</span>
</code></pre>
<h2 id="arrays">Arrays</h2>
<h3 id="defining-arrays">Defining arrays</h3>
<pre class=" language-bash"><code class="prism  language-bash">Fruits<span class="token operator">=</span><span class="token punctuation">(</span><span class="token string">'Apple'</span> <span class="token string">'Banana'</span> <span class="token string">'Orange'</span><span class="token punctuation">)</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">Fruits<span class="token punctuation">[</span>0<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"Apple"</span>
Fruits<span class="token punctuation">[</span>1<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"Banana"</span>
Fruits<span class="token punctuation">[</span>2<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"Orange"</span>
</code></pre>
<h3 id="working-with-arrays">Working with arrays</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> <span class="token variable">${Fruits[0]}</span>           <span class="token comment"># Element #0</span>
<span class="token keyword">echo</span> <span class="token variable">${Fruits[-1]}</span>          <span class="token comment"># Last element</span>
<span class="token keyword">echo</span> <span class="token variable">${Fruits[@]}</span>           <span class="token comment"># All elements, space-separated</span>
<span class="token keyword">echo</span> <span class="token variable">${#Fruits[@]}</span>          <span class="token comment"># Number of elements</span>
<span class="token keyword">echo</span> <span class="token variable">${#Fruits}</span>             <span class="token comment"># String length of the 1st element</span>
<span class="token keyword">echo</span> <span class="token variable">${#Fruits[3]}</span>          <span class="token comment"># String length of the Nth element</span>
<span class="token keyword">echo</span> <span class="token variable">${Fruits[@]:3:2}</span>       <span class="token comment"># Range (from position 3, length 2)</span>
<span class="token keyword">echo</span> <span class="token variable">${!Fruits[@]}</span>          <span class="token comment"># Keys of all elements, space-separated</span>
</code></pre>
<h3 id="operations">Operations</h3>
<pre class=" language-bash"><code class="prism  language-bash">Fruits<span class="token operator">=</span><span class="token punctuation">(</span><span class="token string">"<span class="token variable">${Fruits[@]}</span>"</span> <span class="token string">"Watermelon"</span><span class="token punctuation">)</span>    <span class="token comment"># Push</span>
Fruits+<span class="token operator">=</span><span class="token punctuation">(</span><span class="token string">'Watermelon'</span><span class="token punctuation">)</span>                  <span class="token comment"># Also Push</span>
Fruits<span class="token operator">=</span><span class="token punctuation">(</span> <span class="token variable">${Fruits[@]/Ap*/}</span> <span class="token punctuation">)</span>            <span class="token comment"># Remove by regex match</span>
unset Fruits<span class="token punctuation">[</span>2<span class="token punctuation">]</span>                         <span class="token comment"># Remove one item</span>
Fruits<span class="token operator">=</span><span class="token punctuation">(</span><span class="token string">"<span class="token variable">${Fruits[@]}</span>"</span><span class="token punctuation">)</span>                 <span class="token comment"># Duplicate</span>
Fruits<span class="token operator">=</span><span class="token punctuation">(</span><span class="token string">"<span class="token variable">${Fruits[@]}</span>"</span> <span class="token string">"<span class="token variable">${Veggies[@]}</span>"</span><span class="token punctuation">)</span> <span class="token comment"># Concatenate</span>
lines<span class="token operator">=</span><span class="token punctuation">(</span>`cat <span class="token string">"logfile"</span>`<span class="token punctuation">)</span>                 <span class="token comment"># Read from file</span>
</code></pre>
<h3 id="iteration">Iteration</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> i <span class="token keyword">in</span> <span class="token string">"<span class="token variable">${arrayName[@]}</span>"</span><span class="token punctuation">;</span> <span class="token keyword">do</span>
  <span class="token keyword">echo</span> <span class="token variable">$i</span>
<span class="token keyword">done</span>
</code></pre>
<h2 id="dictionaries">Dictionaries</h2>
<p>{: .-three-column}</p>
<h3 id="defining">Defining</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">declare</span> -A sounds
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">sounds<span class="token punctuation">[</span>dog<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"bark"</span>
sounds<span class="token punctuation">[</span>cow<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"moo"</span>
sounds<span class="token punctuation">[</span>bird<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"tweet"</span>
sounds<span class="token punctuation">[</span>wolf<span class="token punctuation">]</span><span class="token operator">=</span><span class="token string">"howl"</span>
</code></pre>
<p>Declares <code>sound</code> as a Dictionary object (aka associative array).</p>
<h3 id="working-with-dictionaries">Working with dictionaries</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> <span class="token variable">${sounds[dog]}</span> <span class="token comment"># Dog's sound</span>
<span class="token keyword">echo</span> <span class="token variable">${sounds[@]}</span>   <span class="token comment"># All values</span>
<span class="token keyword">echo</span> <span class="token variable">${!sounds[@]}</span>  <span class="token comment"># All keys</span>
<span class="token keyword">echo</span> <span class="token variable">${#sounds[@]}</span>  <span class="token comment"># Number of elements</span>
unset sounds<span class="token punctuation">[</span>dog<span class="token punctuation">]</span>   <span class="token comment"># Delete dog</span>
</code></pre>
<h3 id="iteration-1">Iteration</h3>
<h4 id="iterate-over-values">Iterate over values</h4>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> val <span class="token keyword">in</span> <span class="token string">"<span class="token variable">${sounds[@]}</span>"</span><span class="token punctuation">;</span> <span class="token keyword">do</span>
  <span class="token keyword">echo</span> <span class="token variable">$val</span>
<span class="token keyword">done</span>
</code></pre>
<h4 id="iterate-over-keys">Iterate over keys</h4>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">for</span> key <span class="token keyword">in</span> <span class="token string">"<span class="token variable">${!sounds[@]}</span>"</span><span class="token punctuation">;</span> <span class="token keyword">do</span>
  <span class="token keyword">echo</span> <span class="token variable">$key</span>
<span class="token keyword">done</span>
</code></pre>
<h2 id="options">Options</h2>
<h3 id="options-1">Options</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">set</span> -o noclobber  <span class="token comment"># Avoid overlay files (echo "hi" &gt; foo)</span>
<span class="token keyword">set</span> -o errexit    <span class="token comment"># Used to exit upon error, avoiding cascading errors</span>
<span class="token keyword">set</span> -o pipefail   <span class="token comment"># Unveils hidden failures</span>
<span class="token keyword">set</span> -o nounset    <span class="token comment"># Exposes unset variables</span>
</code></pre>
<h3 id="glob-options">Glob options</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">shopt</span> -s nullglob    <span class="token comment"># Non-matching globs are removed  ('*.foo' =&gt; '')</span>
<span class="token function">shopt</span> -s failglob    <span class="token comment"># Non-matching globs throw errors</span>
<span class="token function">shopt</span> -s nocaseglob  <span class="token comment"># Case insensitive globs</span>
<span class="token function">shopt</span> -s dotglob     <span class="token comment"># Wildcards match dotfiles ("*.sh" =&gt; ".foo.sh")</span>
<span class="token function">shopt</span> -s globstar    <span class="token comment"># Allow ** for recursive matches ('lib/**/*.rb' =&gt; 'lib/a/b/c.rb')</span>
</code></pre>
<p>Set <code>GLOBIGNORE</code> as a colon-separated list of patterns to be removed from glob<br>
matches.</p>
<h2 id="history">History</h2>
<h3 id="commands">Commands</h3>

<table>
<thead>
<tr>
<th>Command</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>history</code></td>
<td>Show history</td>
</tr>
<tr>
<td><code>shopt -s histverify</code></td>
<td>Don’t execute expanded result immediately</td>
</tr>
</tbody>
</table><h3 id="expansions">Expansions</h3>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>!$</code></td>
<td>Expand last parameter of most recent command</td>
</tr>
<tr>
<td><code>!*</code></td>
<td>Expand all parameters of most recent command</td>
</tr>
<tr>
<td><code>!-n</code></td>
<td>Expand <code>n</code>th most recent command</td>
</tr>
<tr>
<td><code>!n</code></td>
<td>Expand <code>n</code>th command in history</td>
</tr>
<tr>
<td><code>!&lt;command&gt;</code></td>
<td>Expand most recent invocation of command <code>&lt;command&gt;</code></td>
</tr>
</tbody>
</table><h3 id="operations-1">Operations</h3>

<table>
<thead>
<tr>
<th>Code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>!!</code></td>
<td>Execute last command again</td>
</tr>
<tr>
<td><code>!!:s/&lt;FROM&gt;/&lt;TO&gt;/</code></td>
<td>Replace first occurrence of <code>&lt;FROM&gt;</code> to <code>&lt;TO&gt;</code> in most recent command</td>
</tr>
<tr>
<td><code>!!:gs/&lt;FROM&gt;/&lt;TO&gt;/</code></td>
<td>Replace all occurrences of <code>&lt;FROM&gt;</code> to <code>&lt;TO&gt;</code> in most recent command</td>
</tr>
<tr>
<td><code>!$:t</code></td>
<td>Expand only basename from last parameter of most recent command</td>
</tr>
<tr>
<td><code>!$:h</code></td>
<td>Expand only directory from last parameter of most recent command</td>
</tr>
</tbody>
</table><p><code>!!</code> and <code>!$</code> can be replaced with any valid expansion.</p>
<h3 id="slices">Slices</h3>

<table>
<thead>
<tr>
<th>Code</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>!!:n</code></td>
<td>Expand only <code>n</code>th token from most recent command (command is <code>0</code>; first argument is <code>1</code>)</td>
</tr>
<tr>
<td><code>!^</code></td>
<td>Expand first argument from most recent command</td>
</tr>
<tr>
<td><code>!$</code></td>
<td>Expand last token from most recent command</td>
</tr>
<tr>
<td><code>!!:n-m</code></td>
<td>Expand range of tokens from most recent command</td>
</tr>
<tr>
<td><code>!!:n-$</code></td>
<td>Expand <code>n</code>th token to last from most recent command</td>
</tr>
</tbody>
</table><p><code>!!</code> can be replaced with any valid expansion i.e. <code>!cat</code>, <code>!-2</code>, <code>!42</code>, etc.</p>
<h2 id="miscellaneous">Miscellaneous</h2>
<h3 id="numeric-calculations">Numeric calculations</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token variable"><span class="token variable">$((</span>a <span class="token operator">+</span> <span class="token number">200</span><span class="token variable">))</span></span>      <span class="token comment"># Add 200 to $a</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token variable"><span class="token variable">$((</span>$RANDOM<span class="token operator">%</span><span class="token number">200</span><span class="token variable">))</span></span>  <span class="token comment"># Random number 0..199</span>
</code></pre>
<h3 id="subshells">Subshells</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token punctuation">(</span>cd somedir<span class="token punctuation">;</span> <span class="token keyword">echo</span> <span class="token string">"I'm now in <span class="token variable">$PWD</span>"</span><span class="token punctuation">)</span>
<span class="token function">pwd</span> <span class="token comment"># still in first directory</span>
</code></pre>
<h3 id="redirection">Redirection</h3>
<pre class=" language-bash"><code class="prism  language-bash">python hello.py <span class="token operator">&gt;</span> output.txt   <span class="token comment"># stdout to (file)</span>
python hello.py <span class="token operator">&gt;&gt;</span> output.txt  <span class="token comment"># stdout to (file), append</span>
python hello.py 2<span class="token operator">&gt;</span> error.log   <span class="token comment"># stderr to (file)</span>
python hello.py 2<span class="token operator">&gt;</span><span class="token operator">&amp;</span>1           <span class="token comment"># stderr to stdout</span>
python hello.py 2<span class="token operator">&gt;</span>/dev/null    <span class="token comment"># stderr to (null)</span>
python hello.py <span class="token operator">&amp;</span><span class="token operator">&gt;</span>/dev/null    <span class="token comment"># stdout and stderr to (null)</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash">python hello.py <span class="token operator">&lt;</span> foo.txt      <span class="token comment"># feed foo.txt to stdin for python</span>
</code></pre>
<h3 id="inspecting-commands">Inspecting commands</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">command</span> -V <span class="token function">cd</span>
<span class="token comment">#=&gt; "cd is a function/alias/whatever"</span>
</code></pre>
<h3 id="trap-errors">Trap errors</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">trap</span> <span class="token string">'echo Error at about <span class="token variable">$LINENO</span>'</span> ERR
</code></pre>
<p>or</p>
<pre class=" language-bash"><code class="prism  language-bash">traperr<span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
  <span class="token keyword">echo</span> <span class="token string">"ERROR: <span class="token variable">${BASH_SOURCE[1]}</span> at about <span class="token variable">${BASH_LINENO[0]}</span>"</span>
<span class="token punctuation">}</span>

<span class="token keyword">set</span> -o errtrace
<span class="token function">trap</span> traperr ERR
</code></pre>
<h3 id="caseswitch">Case/switch</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">case</span> <span class="token string">"<span class="token variable">$1</span>"</span> <span class="token keyword">in</span>
  start <span class="token operator">|</span> up<span class="token punctuation">)</span>
    vagrant up
    <span class="token punctuation">;</span><span class="token punctuation">;</span>

  *<span class="token punctuation">)</span>
    <span class="token keyword">echo</span> <span class="token string">"Usage: <span class="token variable">$0</span> {start|stop|ssh}"</span>
    <span class="token punctuation">;</span><span class="token punctuation">;</span>
esac
</code></pre>
<h3 id="source-relative">Source relative</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">source</span> <span class="token string">"<span class="token variable">${0%/*}</span>/../share/foo.sh"</span>
</code></pre>
<h3 id="printf">printf</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">printf</span> <span class="token string">"Hello %s, I'm %s"</span> Sven Olga
<span class="token comment">#=&gt; "Hello Sven, I'm Olga</span>

<span class="token function">printf</span> <span class="token string">"1 + 1 = %d"</span> 2
<span class="token comment">#=&gt; "1 + 1 = 2"</span>

<span class="token function">printf</span> <span class="token string">"This is how you print a float: %f"</span> 2
<span class="token comment">#=&gt; "This is how you print a float: 2.000000"</span>
</code></pre>
<h3 id="directory-of-script">Directory of script</h3>
<pre class=" language-bash"><code class="prism  language-bash">DIR<span class="token operator">=</span><span class="token string">"<span class="token variable">${0%/*}</span>"</span>
</code></pre>
<h3 id="getting-options">Getting options</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">while</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> <span class="token string">"<span class="token variable">$1</span>"</span> <span class="token operator">=</span>~ ^- <span class="token operator">&amp;&amp;</span> <span class="token operator">!</span> <span class="token string">"<span class="token variable">$1</span>"</span> <span class="token operator">==</span> <span class="token string">"--"</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">do</span> <span class="token keyword">case</span> <span class="token variable">$1</span> <span class="token keyword">in</span>
  -V <span class="token operator">|</span> --version <span class="token punctuation">)</span>
    <span class="token keyword">echo</span> <span class="token variable">$version</span>
    <span class="token keyword">exit</span>
    <span class="token punctuation">;</span><span class="token punctuation">;</span>
  -s <span class="token operator">|</span> --string <span class="token punctuation">)</span>
    <span class="token function">shift</span><span class="token punctuation">;</span> string<span class="token operator">=</span><span class="token variable">$1</span>
    <span class="token punctuation">;</span><span class="token punctuation">;</span>
  -f <span class="token operator">|</span> --flag <span class="token punctuation">)</span>
    flag<span class="token operator">=</span>1
    <span class="token punctuation">;</span><span class="token punctuation">;</span>
esac<span class="token punctuation">;</span> <span class="token function">shift</span><span class="token punctuation">;</span> <span class="token keyword">done</span>
<span class="token keyword">if</span> <span class="token punctuation">[</span><span class="token punctuation">[</span> <span class="token string">"<span class="token variable">$1</span>"</span> <span class="token operator">==</span> <span class="token string">'--'</span> <span class="token punctuation">]</span><span class="token punctuation">]</span><span class="token punctuation">;</span> <span class="token keyword">then</span> <span class="token function">shift</span><span class="token punctuation">;</span> <span class="token keyword">fi</span>
</code></pre>
<h3 id="heredoc">Heredoc</h3>
<pre class=" language-sh"><code class="prism  language-sh">cat &lt;&lt;END
hello world
END
</code></pre>
<h3 id="reading-input">Reading input</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">echo</span> -n <span class="token string">"Proceed? [y/n]: "</span>
<span class="token function">read</span> ans
<span class="token keyword">echo</span> <span class="token variable">$ans</span>
</code></pre>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">read</span> -n 1 ans    <span class="token comment"># Just one character</span>
</code></pre>
<h3 id="special-variables">Special variables</h3>

<table>
<thead>
<tr>
<th>Expression</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>$?</code></td>
<td>Exit status of last task</td>
</tr>
<tr>
<td><code>$!</code></td>
<td>PID of last background task</td>
</tr>
<tr>
<td><code>$$</code></td>
<td>PID of shell</td>
</tr>
<tr>
<td><code>$0</code></td>
<td>Filename of the shell script</td>
</tr>
</tbody>
</table><p>See <a href="http://wiki.bash-hackers.org/syntax/shellvars#special_parameters_and_shell_variables">Special parameters</a>.</p>
<h3 id="go-to-previous-directory">Go to previous directory</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">pwd</span> <span class="token comment"># /home/user/foo</span>
<span class="token function">cd</span> bar/
<span class="token function">pwd</span> <span class="token comment"># /home/user/foo/bar</span>
<span class="token function">cd</span> -
<span class="token function">pwd</span> <span class="token comment"># /home/user/foo</span>
</code></pre>
<h3 id="check-for-commands-result">Check for command’s result</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> <span class="token function">ping</span> -c 1 google.com<span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"It appears you have a working internet connection"</span>
<span class="token keyword">fi</span>
</code></pre>
<h3 id="grep-check">Grep check</h3>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token keyword">if</span> <span class="token function">grep</span> -q <span class="token string">'foo'</span> ~/.bash_history<span class="token punctuation">;</span> <span class="token keyword">then</span>
  <span class="token keyword">echo</span> <span class="token string">"You appear to have typed 'foo' in the past"</span>
<span class="token keyword">fi</span>
</code></pre>

