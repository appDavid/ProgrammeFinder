PHP ProgrammeFinder
===============

  Begin  entering  a  string  into  a  text  box  to  search  on  and  pause.   Given  I  am  on  a  Web  Page   When  I  begin  typing  a  Search  String  into  a  Text  Box  and  stop   And  there  are  brand  names  that  contain  the  string  I  have  typed   Then  I  should  be  dynamically  shown  a  list  of  those  brands
  
  
  
<?php
$str = preg_replace('~[^a-zA-Z0-9]+~', '', $str);


// get the q parameter from URL
$q=$_REQUEST["q"]; $hint="";

// lookup all hints from array if $q is different from "" 
if ($q !== "") {
  $q=strtolower($q); $len=strlen($q);
  foreach($a as $name) {
    if (stristr($q, substr($name,0,$len))) {
      if ($hint==="") {
        $hint=$name;
      } else {
        $hint .= ", $name";
      }
    }
  }
}

// Output "no suggestion" if no hint was found
// or output the correct values 
echo $hint==="" ? "no suggestion" : $hint;
?>
