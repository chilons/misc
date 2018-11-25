<!DOCTYPE html>
<html>

<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Kakka React Coding Convention</title>
  <link rel="stylesheet" href="https://stackedit.io/style.css" />
</head>

<body class="stackedit">
  <div class="stackedit__html"><h1 id="kakka-react-coding-convention">Kakka React Coding Convention</h1>
<ul>
<li>
<p>Only use <em>const</em> for global constants and Pure Components</p>
<pre><code>// don't do this
const { profile } = this.state;
const list = this.getList();

// do this, use let for local variables
let { profile } = this.state;
let list = this.getList();

// use const for constants
const LIMIT = 20;

// use const for Pure Components
export const ProfileName = ({ profile }) =&gt; {
  return &lt;span&gt;{profile.name}&lt;/span&gt;;
};
</code></pre>
</li>
<li>
<p>Function syntax:</p>
<ul>
<li>Use <code>function doSomething()</code> for utility global functions, use <code>const Something = ({propA}) =&gt; {}</code> for Pure Components</li>
<li>Class method syntax:
<ul>
<li>Use babel’s arrow method syntax<pre><code>   handleSomething = something =&gt; { // do stuff }
</code></pre>
for <em>onSomething</em> and <em>handleSomething</em> methods, and other methods that require binding</li>
</ul>
</li>
</ul>
</li>
<li>
<p>Naming</p>
<ul>
<li>
<p>Don’t use verbs as class names</p>
</li>
<li>
<p>Method and function names must be verbs, use <em>getSomething</em> if needed</p>
</li>
<li>
<p>For local handler methods to pass to <em>onSomeEvent</em> properties, name them <em>handleSomething</em>. Example:</p>
<pre><code>    handleCancel = e =&gt; { // do stuff }
    handleSubmit = e =&gt; { // do stuff }
    render() {
        return &lt;div&gt;
            &lt;Button onClick={this.handleCancel}&gt;Cancel&lt;/Button&gt;
            &lt;Button type="submit" onClick={this.handleSubmit}&gt;Submit&lt;/Button&gt;
        &lt;/div&gt;
    }
</code></pre>
</li>
<li>
<p>For methods and properties that are called when something is done, e.g an HTTP request, name them <code>onSomething</code> at present tense (no ‘ed’)</p>
<pre><code>    onLoadProfile = profile =&gt; { // do stuff }
    load() {
        getProfile.then(this.onLoadProfile)
    }
    handleDelete = () =&gt; {
        let {onDelete, entry} = this.props
        onDelete &amp;&amp; onDelete(entry)
    }
    render() {
        return &lt;Button onClick={this.handleDelete}/&gt;
    }
</code></pre>
</li>
</ul>
</li>
</ul>
</div>
</body>

</html>
