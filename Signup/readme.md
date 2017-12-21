---


---

<h1 id="signup-page">Signup page</h1>
<p>Link Zeplin :
CS - User - Sign Up
CS - User - Sign Up error</p>
<h1 id="define-action">Define Action</h1>
<p>ACTION_REGISTER_REQUEST</p>
<p>ACTION_REGISTER_FAILURE</p>
<p>ACTION_REGISTER_SUCCESS</p>
<p>when click on button " Create Account"</p>
<ul>
<li>Define constants
src/routes/user_register/actions.js</li>
</ul>
<pre class=" language-js"><code class="prism  language-js"><span class="token keyword">export</span> <span class="token keyword">const</span> ACTION_REGISTER_REQUEST <span class="token operator">=</span> <span class="token string">"action_register_request"</span><span class="token punctuation">;</span>
<span class="token keyword">export</span> <span class="token keyword">const</span> ACTION_REGISTER_SUCCESS <span class="token operator">=</span> <span class="token string">"action_register_success"</span><span class="token punctuation">;</span>
<span class="token keyword">export</span> <span class="token keyword">const</span> ACTION_REGISTER_FAILURE <span class="token operator">=</span> <span class="token string">"action_register_failure"</span><span class="token punctuation">;</span>## Create files and folders
</code></pre>
<h2 id="determine-components">Determine components</h2>
<p>All components and container write in :
src/routes/user_register/containers/SignupPage.js</p>
<ul>
<li>import required components: TextField, RaisedButton, CheckBox</li>
<li>declare and set default value for component’s propTypes: username, email, password, isAgreeTerms</li>
<li>export component with style :</li>
</ul>
<pre class=" language-js"><code class="prism  language-js"><span class="token keyword">export</span> <span class="token keyword">default</span> <span class="token function">withStyles</span><span class="token punctuation">(</span>s<span class="token punctuation">)</span><span class="token punctuation">(</span><span class="token function">connect</span><span class="token punctuation">(</span>mapStateToProps<span class="token punctuation">,</span> mapDispatchToProps<span class="token punctuation">)</span><span class="token punctuation">(</span>SignupPage<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<p>LoginPage.oscss : contain the styles for current component</p>
<pre class=" language-js"><code class="prism  language-js"><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token operator">/</span><span class="token punctuation">.</span><span class="token punctuation">.</span><span class="token operator">/</span>resources<span class="token operator">/</span>scss<span class="token operator">/</span>LoginPage<span class="token punctuation">.</span>oscss
</code></pre>
<h2 id="determine--implement-containers">Determine &amp; implement containers</h2>
<ul>
<li>determine container states:</li>
</ul>
<pre class=" language-js"><code class="prism  language-js"><span class="token keyword">this</span><span class="token punctuation">.</span>state <span class="token operator">=</span> <span class="token punctuation">{</span>
      username<span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
      email<span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
      password<span class="token punctuation">:</span> <span class="token string">""</span><span class="token punctuation">,</span>
      isAgreeTerms<span class="token punctuation">:</span> <span class="token boolean">false</span><span class="token punctuation">,</span>
    <span class="token punctuation">}</span><span class="token punctuation">;</span>
</code></pre>
<ul>
<li>render container states:</li>
</ul>
<pre class=" language-js"><code class="prism  language-js"><span class="token function">render</span><span class="token punctuation">(</span><span class="token punctuation">)</span> <span class="token punctuation">{</span>
    <span class="token keyword">return</span> <span class="token punctuation">(</span>
      <span class="token operator">&lt;</span><span class="token operator">...</span><span class="token punctuation">.</span>
			<span class="token operator">&lt;</span>TextField
                label<span class="token operator">=</span><span class="token string">"Username"</span>
                type<span class="token operator">=</span><span class="token string">"email"</span>
                className<span class="token operator">=</span><span class="token string">"mdl-input"</span>
                floatingLabel                value<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>username<span class="token punctuation">}</span>
                onChange<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>handleInputChange<span class="token punctuation">}</span>
              <span class="token operator">/</span><span class="token operator">&gt;</span>
              <span class="token operator">&lt;</span>TextField
                label<span class="token operator">=</span><span class="token string">"Email"</span>
                type<span class="token operator">=</span><span class="token string">"email"</span>
                className<span class="token operator">=</span><span class="token string">"mdl-input"</span>
                floatingLabel
                value<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>email<span class="token punctuation">}</span>
                onChange<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>handleInputChange<span class="token punctuation">}</span>
              <span class="token operator">/</span><span class="token operator">&gt;</span>
              <span class="token operator">&lt;</span>TextField
                value<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>password<span class="token punctuation">}</span>
                onChange<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>handleInputChange<span class="token punctuation">}</span>
                label<span class="token operator">=</span><span class="token string">"Password"</span>
                type<span class="token operator">=</span><span class="token string">"password"</span>
                className<span class="token operator">=</span><span class="token string">"mdl-input"</span>
                floatingLabel
              <span class="token operator">/</span><span class="token operator">&gt;</span>
              <span class="token operator">&lt;</span>TextField
                value<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>password<span class="token punctuation">}</span>
                onChange<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>handleInputChange<span class="token punctuation">}</span>
                label<span class="token operator">=</span><span class="token string">"Retype Password"</span>
                type<span class="token operator">=</span><span class="token string">"password"</span>
                className<span class="token operator">=</span><span class="token string">"mdl-input"</span>
                floatingLabel
              <span class="token operator">/</span><span class="token operator">&gt;</span>
              <span class="token operator">&lt;</span>CheckBox
              className<span class="token operator">=</span><span class="token string">"remember-checkbox"</span>
              label<span class="token operator">=</span><span class="token string">"I agree to all Terms &amp; Conditions"</span>
              checked<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>state<span class="token punctuation">.</span>isRememberMe<span class="token punctuation">}</span>
              onChange<span class="token operator">=</span><span class="token punctuation">{</span><span class="token keyword">this</span><span class="token punctuation">.</span>handleInputChange<span class="token punctuation">}</span>
            <span class="token operator">/</span><span class="token operator">&gt;</span>
			<span class="token punctuation">)</span>
		<span class="token punctuation">}</span>
</code></pre>
<ul>
<li>make the container to work with Redux</li>
</ul>
<pre class=" language-js"><code class="prism  language-js"><span class="token keyword">const</span> mapStateToProps <span class="token operator">=</span> <span class="token punctuation">(</span><span class="token punctuation">{</span> username<span class="token punctuation">,</span> email<span class="token punctuation">,</span> password<span class="token punctuation">,</span> isAgreeTerms <span class="token punctuation">}</span><span class="token punctuation">)</span> <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token punctuation">(</span><span class="token punctuation">{</span>
  username<span class="token punctuation">,</span>
  email<span class="token punctuation">,</span>
  password<span class="token punctuation">,</span>
  isAgreeTerms<span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>

<span class="token keyword">const</span> mapDispatchToProps <span class="token operator">=</span> dispatch <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token punctuation">(</span><span class="token punctuation">{</span>
  register<span class="token punctuation">:</span> cred <span class="token operator">=</span><span class="token operator">&gt;</span> <span class="token function">dispatch</span><span class="token punctuation">(</span><span class="token function">register</span><span class="token punctuation">(</span>cred<span class="token punctuation">)</span><span class="token punctuation">)</span><span class="token punctuation">,</span>
<span class="token punctuation">}</span><span class="token punctuation">)</span><span class="token punctuation">;</span>
</code></pre>
<h2 id="delete-a-file">Delete a file</h2>
<p>You can delete the current file by clicking the <strong>Remove</strong> button in the file explorer. The file will be moved into the <strong>Trash</strong> folder and automatically deleted after 7 days of inactivity.</p>
<pre><code>const route = await new Promise(resolve =&gt; {
          require.ensure(
            [],
            require =&gt; resolve(require("./routes/SignupPageRoute").default),
            "signuppage",
          );
        });

        const component = await route(context, true);
        return {
          title: "Sign Up Page",
          chunk: "signuppage",
          enableServerSideRender: false,
          component,
        };
</code></pre>

