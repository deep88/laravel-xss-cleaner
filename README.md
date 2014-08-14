laravel-xss-cleaner
===================

Fast, simple &amp; effective way to clean users' inputs for laravel PHP framework.

### Installation
Because of the simplicity of the class you can include it within your models folder under `/app/models`

### Usage
The Laravel-XSS-Cleaner is very easy to use and it supports the object oriented notation. Let's take a very basic example:

```
{{Form::open(['route' => 'posts.create'])}}
{{Form::text('title')}}
{{Form::textarea('body')}}
{{Form::close()}}
```

```
$rules = ['title' => 'required|min:13', 'body' => 'required|min:150'];
$validator = Validator(Input::all(), $rules);

if($validator->passes()){
  $xss = new XSS;
  $xss->clean(Input::al());
  $input = $xss->get();
  
  $post = new Post;
  $post->title = $input->title;
  $post->body = $input->body;
  
  // to test the results you can dd($input); & happy coding everyone!
}
```
