---
title: "nameof (refer&#234;ncia do C# e do Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# nameof (refer&#234;ncia do C# e do Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Usado para obter o nome de cadeia de caracteres simples \(não qualificado\) de uma variável, tipo ou membro.  Quando o relatório de erros no código, conectando links do model\-view\-controller \(MVC\), acionar eventos de propriedade alterada, etc., geralmente é necessário capturar o nome de cadeia de caracteres de um método.  Usando `nameof` Ajuda a manter seu código válido ao renomear definições.  Antes era usar literais de cadeia de caracteres para se referir às definições, que é frágil ao renomear os elementos de código porque não sabe ferramentas para verificar esses literais de cadeia de caracteres.  
  
 Um `nameof` expressão tem este formato:  
  
```c#  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode”  
  
```  
  
## Principais casos de uso  
 Esses exemplos mostram os casos de uso de chave `nameof`.  
  
 Valide parâmetros:  
 ```c#  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
  
```  
  
 Links de ação do MVC:  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
  
```  
  
 INotifyPropertyChanged:  
 ```c#  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
  
```  
  
 Propriedade de dependência XAML:  
 ```c#  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
  
```  
  
 Log:  
 ```c#  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
  
```  
  
 Atributos:  
 ```c#  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## Exemplos  
 Alguns exemplos de c\#:  
  
```c#  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
nameof(C) -> "C"  
nameof(C.Method1) -> "Method1"   
nameof(C.Method2) -> "Method2"  
nameof(c.Method1) -> "Method1"   
nameof(c.Method2) -> "Method2"  
nameof(z) -> "z" // inside of Method2 ok, inside Method1 is a compiler error  
nameof(Stuff) = "Stuff"  
nameof(T) -> "T" // works inside of method but not in attributes on the method  
nameof(f) -> “f”  
nameof(f<T>) -> syntax error  
nameof(f<>) -> syntax error  
nameof(Method2()) -> error “This expression does not have a name”  
  
```  
  
 Muitos dos exemplos acima se aplicam ao Visual Basic.  Aqui estão alguns exemplos específicos do Visual Basic:  
  
```vb  
NameOf(a!Foo) -> ' error  "This expression does not have a name"  
NameOf(dict("Foo")) -> ' error  "This expression does not have a name": default property access  
NameOf(dict.Item("Foo")) -> ' error  "This expression does not have a name"  
NameOf(arr(2)) -> ' error  "This expression does not have a name": array element index  
Dim x = Nothing   
NameOf(x.ToString(2)) -> ' error  "This expression does not have a name"  
Dim o = Nothing  
NameOf(o.Equals) -> ' result "Equals".  Warning: "Access of static member of instance; instance will not be evaluated"  
  
```  
  
## Observações  
 O argumento `nameof` deve ser um nome simples, nome qualificado, acesso de membro, acesso básico com um membro especificado ou esse acesso com um membro especificado.  A expressão de argumento identifica uma definição de código, mas nunca será avaliado.  
  
 Como o argumento deve ser uma expressão sintaticamente, há muitas coisas não permitidas que não são úteis para a lista.  O seguinte valem a pena mencionar que geram erros: tipos predefinidos \(por exemplo, `int` ou `void`\), tipos anuláveis \(`Point?`\), tipos de matriz \(`Customer[,]`\), tipos de ponteiro \(`Buffer*`\) e alias qualificado \(`A::B`\) e não associadas a tipos genéricos \(`Dictionary<,>`\), símbolos de pré\-processamento \(`DEBUG`\) e rótulos \(`loop:`\).  
  
 Se você precisar obter o nome totalmente qualificado, você pode usar o `typeof` expressão juntamente com `nameof`.  
  
 Nos exemplos a você ver o que você pode usar um nome de tipo e acessar um nome de método de instância.  Você não precisa ter uma instância do tipo, como necessário em expressões avaliadas.  Usando o nome de tipo pode ser muito prático em algumas situações e uma vez que apenas você está referenciando o nome e não usando dados de instância, você não precisa contrive uma expressão ou uma variável de instância.  
  
 Você pode fazer referência os membros de uma classe em expressões de atributo na classe.  
  
 Não é possível obter uma informações de assinaturas, como "`Method1 (str, str)`".  Uma maneira de fazer isso é usar uma expressão, `Expression e = () => A.B.Method1("s1", "s2")`, e puxe MemberInfo da árvore de expressão resultante.  
  
## Especificações da linguagem  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
 Para obter mais informações, consulte o [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md).  
  
## Consulte também  
 [Referência de C\#](../../../csharp/language-reference/index.md)   
 [Guia de Programação em C\#](../../../csharp/programming-guide/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [Referência da linguagem Visual Basic](../../../visual-basic/language-reference/index.md)   
 [Guia de programação do Visual Basic](../../../visual-basic/programming-guide/index.md)