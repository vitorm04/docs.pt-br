---
title: nameof (Referência de C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 2695095aa4bf2035d8766f3cbcb82f4fbb290e22
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207831"
---
# <a name="nameof-c-reference"></a>nameof (Referência de C#)

Usado para obter o nome de cadeia de caracteres simples (não qualificado) de uma variável, tipo ou membro.  

Ao relatar erros no código, conectar links de MVC (Modelo-Exibição-Controlador), disparando eventos de propriedade alterada etc., normalmente você captura o nome da cadeia de caracteres de um método.  Usar `nameof` ajuda a manter seu código válido ao renomear definições.  Antes era necessário usar literais de cadeia de caracteres para se referir às definições, o que é frágil ao renomear os elementos de código porque as ferramentas não sabem verificar esses literais de cadeia de caracteres.  
  
 Uma expressão `nameof` tem este formato:  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a>Principais casos de uso  
 Esses exemplos mostram os principais casos de uso para `nameof`.  
  
 Validar parâmetros:  
 ```csharp  
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
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 Propriedade de dependência XAML:  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 Registrando em log:  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 Atributos:  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a>Exemplos  
 Alguns exemplos de C#:  
  
```csharp  
using Stuff = Some.Cool.Functionality  
class C {  
    static int Method1 (string x, int y) {}  
    static int Method1 (string x, string y) {}  
    int Method2 (int z) {}  
    string f<T>() => nameof(T);  
}  
  
var c = new C()  
  
class Test {  
    static void Main (string[] args) {  
        Console.WriteLine(nameof(C)); // -> "C"  
        Console.WriteLine(nameof(C.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(C.Method2)); // -> "Method2"  
        Console.WriteLine(nameof(c.Method1)); // -> "Method1"   
        Console.WriteLine(nameof(c.Method2)); // -> "Method2"  
        // Console.WriteLine(nameof(z)); -> "z" [inside of Method2 ok, inside Method1 is a compiler error]  
        Console.WriteLine(nameof(Stuff)); // -> "Stuff"  
        // Console.WriteLine(nameof(T)); -> "T" [works inside of method but not in attributes on the method]  
        Console.WriteLine(nameof(f)); // -> "f"  
        // Console.WriteLine(nameof(f<T>)); -> [syntax error]  
        // Console.WriteLine(nameof(f<>)); -> [syntax error]  
        // Console.WriteLine(nameof(Method2())); -> [error "This expression does not have a name"]  
    }
}
```  
  
## <a name="remarks"></a>Comentários  
 O argumento para `nameof` deve ser um nome simples, nome qualificado, acesso de membro, acesso básico com um membro especificado ou esse acesso com um membro especificado.  A expressão de argumento identifica uma definição de código, mas ela nunca é avaliada.  
  
 Como o argumento deve ser uma expressão sintaticamente, há muitas coisas não permitidas que não são úteis para a lista.  Os itens a seguir são os que valem a pena mencionar que produzem erros: tipos predefinidos (por exemplo, `int` ou `void`), tipos que permitem valor nulo (`Point?`), tipos de matriz (`Customer[,]`), tipos de ponteiro (`Buffer*`), alias qualificado (`A::B`) e tipos genéricos não associados (`Dictionary<,>`), símbolos de pré-processamento (`DEBUG`) e rótulos (`loop:`).  
  
 Se você precisar obter o nome totalmente qualificado, poderá usar expressão `typeof` juntamente com `nameof`.  Por exemplo:
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 Infelizmente `typeof` não é uma expressão de constante como `nameof`, então `typeof` não pode ser usada em conjunto com `nameof` em todos os mesmos locais como `nameof`.  Por exemplo, o seguinte poderia causar um erro de compilação CS0182:
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 Nos exemplos você vê que pode usar um nome de tipo e acessar um nome de método de instância.  Você não precisa ter uma instância do tipo, como necessário nas expressões avaliadas.  Usar o nome do tipo pode ser muito conveniente em algumas situações e como você está fazendo referência ao nome e não usando os dados da instância, não precisa criar uma variável de instância ou expressão.  
  
 Você pode fazer referência aos membros de uma classe em expressões de atributo na classe.  
  
 Não é possível obter as informações de uma assinaturas como "`Method1 (str, str)`".  Uma maneira de fazer isso é usar uma expressão, `Expression e = () => A.B.Method1("s1", "s2")` e efetuar o pull de MemberInfo da árvore de expressão resultante.  
  
## <a name="language-specifications"></a>Especificações da linguagem  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [typeof](../../../csharp/language-reference/keywords/typeof.md)  
 
