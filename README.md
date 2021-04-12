# Best Pratics in C#
A guide for best pratics in C# Language


#  Introdução

A seguir serão listados exemplos de boas práticas em C#, para isso iremos utilizar duas regras de ouro a serem seguidas para atingir bons padrões de codificação. São elas:

	* Convenções de nomenclatura

	* Otimização da sintaxe

	
# Convenções de Nomenclatura

As convenções de nomenclatura referem-se à declaração de variáveis.

Devemos sempre usar camelCase ao declarar variáveis, por exemplo, var itemList = new List <T> ();

 Para declarar uma variável que retorna uma única entidade/objeto, use a seguinte convenção:
 
 ``` cs
 
 var item = new Item();
 
 ```
 
 Para declarar uma variável que retorna várias entidades/objetos, é necessário adicionar o sufixo "s" ou "List", para que possamos identificar facilmente que ela retornará uma lista de classes/objetos:
 
  ``` cs
  
	var items = new List<Item>();   
	//or  
	var itemList = new List<Item>();  
 
 ```
 
 Para declarar uma variável privada, usamos um sublinhado(underline) (_)
 
 
   ``` cs
   
   private int _value = 10;  
   
   ```
   
# Tabela de convenções de nomenclatura
   
Nome      |Case
--------- | ------
Variáveis | camelCase
Classe    | PascalCase
Construtor | PascalCase
Propriedades | PascalCase
Delegar | PascalCase
Enum | PascalCase
Argumentos em métodos | camelCase
Método | PascalCase
Constantes|  PascalCase
Campo | camelCase
   
# Otimizando a sintaxe

Para declarar um método vazio que retorna apenas uma visão no MVC, devemos usar o corpo da expressão


``` cs

//Evite  
public ActionResult Dashboard()  
{  
    return View();  
}  

//Use  
public ActionResult Dashboard() => View(); 

```

Para verificar se há condições nulas ou vazias, use o seguinte:

``` cs

//Evite  
var varName = "faisal";  
if (varName != null && varName != "")  
{  
   //code  
}  

//Use  
var varName = "faisal";  
if (!string.IsNullOrEmpty(varName))  
{  
    //code  
}  

```

Abaixo está como usar a expressão coalescente nula:

``` cs

Test test = new Test();  

//Evite  
var varName = test.Name != null ? test.Name : "";  

//Use  
var varName = test.Name ?? ""; 

```

Abaixo está como usar o inicializador de objeto:

``` cs

//Evite  
Test test = new Test();  
test.Id = 1;  
test.Name = "faisal";  

//Use  
var test = new Test  
{  
   Id = 1,  
   Name = "faisal"  
};  

```
Abaixo está como usar o operador trenário "?":

``` cs

//Evite  
var empName = "";  
Session["Name"] = "Faisal Pathan";  
if (Session["Name"] != null)  
{  
   empName = Session["Name"].ToString();  
}  
else  
{  
     empName = "";  
}  

//Use  
var empName = "";  
Session["Name"] = "Faisal Pathan";  
empName = Session["Name"]?.ToString() ?? "";

```

Evitar chaves extras também é uma prática a ser adotada. Trabalhe apenas com instruções de uma única linha:

``` cs

var count = 10;  

//Evite  
 if (count > 0)  
{  
   //code  
   count++;  
}  


//Use  
 if (count > 0) count++; //code  


//Evite  
for (int i = 0; i < count; i++)  
{  
   //code  
   count += 10;  
}  

//Use
for (int i = 0; i < count; i++) count += 10;  


var testList = new List<Test>();  
var names = new ArrayList();  

//Evite  
foreach (var item in testList)  
{  
   names.Add(item.Name);  
}  

//Use  
foreach (var item in testList) names.Add(item.Name);

```
   
 Abaixo está como usar a interpolação de string:  
 
 ``` cs
 
 Test test = new Test();  

//Evite  
 var details = string.Format("{0}, you are welcome, Your Id is {1}", test.Name , test.Id + "_emp");  

//Use  
var details = $"{test.Name}, you are welcome, Your Id is {test.Id}_emp";
 
 ```
 
Este último bloco de código demonstra como usar a nova caixa de comando leve introduzida no C # 8:

``` cs

int itemSwitch = 1;  

//Bom  
switch (itemSwitch)  
{  
 case 1:  
 Console.WriteLine("Item 1");  
 break;  
 case 2:  
 Console.WriteLine("Item 2");  
 break;  
 default:  
 Console.WriteLine("Item case");  
 break;  
}  

//Melhor  
 var message = itemSwitch switch   
            {  
                1 =>  Console.WriteLine("Item 1"),  
                2 =>  Console.WriteLine("Item 2"),  
                2 =>  Console.WriteLine("Item 3")  
            };

```
