<h1>MOM (Media Ordering Mixin)</h1>
<p>Coming up before 2017 (I hope)</p>
<img src="https://cloud.githubusercontent.com/assets/1699461/18881869/4c4a8a08-84dd-11e6-81e9-62b77addc188.jpg" width="100%"/>

<h2>Breakpoints</h2>
````SCSS
$breakpoints:(
    small  : (max-width: 480px),
    medium : (max-width: 640px),
    large  : (max-width: 960px)              
);

````

<h2>Stuff to include</h2> 
````SCSS
//  Convert number to ratio  ratio(1.7777778) =>   16/9 
@function ratio($x, $y: null){
    @if not $y {
        $n: $x; $y: 1;
        @while $y < 10 {
            $x:  $n * 10 - ((10 - $y) * $n);
            @if $x == round($x){ @return #{$x}/#{$y}; }  
            @else { $y: $y + 1; }
        }
        $x: round($n * 1000000); $y: 1000000;
        @while $x % 10 == 0 { $x: $x/10; $y: $y/10; } 
        @while $x % 5 == 0 { $x: $x/5; $y: $y/5; } 
        @while $x % 2 == 0 { $x: $x/2; $y: $y/2; } 
        @return #{$x}/#{$y};
    } 
    @else if $x == round($x) and $y == round($y){ @return #{$x}/#{$y}; }
    @warn 'X and Y must be integers'; @return false;
}
````
