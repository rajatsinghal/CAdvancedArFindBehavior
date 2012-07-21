CAdvancedArFindBehavior

The CAdvancedArFindBehavior extension adds up some functionality to the default possibilites of yii´s ActiveRecord implementation.
 
To use this extension, just copy this file to your extensions/ directory,

add 'import' => 'application.extensions.CAdvancedArFindBehavior', [...] to your config/main.php and

add this behavior to each model you would like to inherit the new possibilities:
 
 * public function behaviors(){
 *         return array( 'CAdvancedArFindBehavior' => array(
 *           'class' => 'application.extensions.CAdvancedArFindBehavior')); 
 *         }

 This extension is useful when you need array of values of a particular attribute based on some condition, and 
 loading whole  objects for them is not only big data pull and hense slow, but also it's more code, as you will 
 have to traverse through all the objects and foreach of them put the required attrute's value in the array, and 
 then proceed with it...

 With this extension you have one function similar to findAll, in which one extra attribute column to select you 
 need to provide, and it return array containing all row's values for that attribute.

 This is a similar function to pluck of ruby on rails.

** Syntex **
 * public array findColumn(string $column, mixed $condition='', array $params=array()) {}

 
 ** Things to Notice **
 * `beforeFind`, `afterFind` functions also will be ignored.
 * Scopes will work as normal.


** Example **

    *$active_users_emails = User::model()->findColumn('email', 'active = 1');
   
    returns array('rajat@gmail.com','rajatsinghal@gmail.com').. 
    which is emails of all users who have active field as 1.

=======================