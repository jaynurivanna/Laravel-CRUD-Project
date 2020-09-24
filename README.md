<p align="center"><a href="https://laravel.com" target="_blank"><img src="https://raw.githubusercontent.com/laravel/art/master/logo-lockup/5%20SVG/2%20CMYK/1%20Full%20Color/laravel-logolockup-cmyk-red.svg" width="400"></a></p>

<h3>Welcome to my first laravel project study using CRUD function</h3>
<h5> Step 1 Installation Laravel </h5>
<p> Open cmd and directed to our location, like mine I do in c:/xampp/htdocs <pre>composer create-project --prefer-dist laravel/laravel blog</pre></p>
<h5> Step 2 Database Configuration </h5>
<p> We need to do the db connection at .env file enter the your own information such as database name, username, password <pre>
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laravelblog
DB_USERNAME=root
DB_PASSWORD=
</pre></p>
<h5> Step 3 Create Migration</h5>
<p> What we going to do here is want to create the database table use this command <pre>php artisan make:migration create_products_table --create=products</pre></p>
<p> Now in our database/migration we need to add lines of codes for create products table <pre> 
public function up()
    {
        Schema::create('products', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->text('detail');
            $table->timestamps();
        });
    }
 </pre></p>
 <p> Now we need to run the migration use command <pre>php artisan migrate</pre></p>
 <h5> Step 4 Add Route </h5>
 <p> Open route/web.app then add this route<pre>Route::resource('products','ProductController');</pre> so it will directed to our Products page</p>
 <h5> Step 5 Add Controller and Model </h5>
 <p><pre>php artisan make:controller ProductController --resource --model=Product</pre> in this controller will have all the function by default have seven functions</p>
 <ol>
  <li>index()</li>
  <li>create()</li>
  <li>store()</li>
  <li>show()</li>
  <li>edit()</li>
  <li>update()</li>
  <li>destroy()</li>
</ol>
<h5>Step 6 Add Blade Files</h5>
<p>We add new folder name products in <h6>resources/views/</h6> we create the files based on the controller and model we create before</p>
<p>Here all the HTML files and front end code will be here</p>
<h5> Now we can run our project! By run this command <pre>php artisan serve</pre></h5>
<p>http://localhost:8000/products open this url and see the results!</p>

<h4> Further Understanding in CRUD Function</h4>
<pre>app/http/controller/ProductController.php</pre><p>All the 7 default functions located and can be call as<b> Controller File</b></p>
<pre>routes/web.php</pre><p>The routes for product page</p>
<h5>Insert Data in Laravel</h5>
<p>The view file (resources/views/create.blade.php)</p>
<p>The Model File(app/Providers/product.php)</p>
<p>In form action we add the route so it will process the function that we use<pre>form action="{{ route('products.store') }}" method="POST"</pre></p>
<h5>Retrieve Data in Laravel</h5>
<p>The view file (resources/views/view.blade.php)</p>
<p>In form data field we add the code and it will display the data from db<pre>{{ $product->name }}</pre></p>
<h5>Update Data in Laravel</h5>
<p>The view file (resources/views/edit.blade.php)</p>
<p>In form action we add routes, as we know here it will bring product id as unique key so it will edit the correct product<pre>{{ route('products.update',$product->id) }}</p>
<h5>Delete Data in Laravel</h5>
<p><pre>Here to delete it use<pre> @method('DELETE')</pre><p>
<p>In form action we add routes,it will bring product id same like when update so it will delete the correct product<pre>{{ route('products.destroy',$product->id) }}</p>
<h5>Here some meaning for function use in Laravel</h5>
<pre>@csrf -> it will protect our apps from Cross Site Request Forgery attacks, it will create csrf token for each active session to verify auntheticated user</pre>
<pre>Since Laravel 5.6 to delete and put function using tag -> @method("DELETE") and @method("PUT")</pre>
<pre>@extends -> use to 'extend' the template and the template can extend using own section using -> @yield</pre>
 
  
