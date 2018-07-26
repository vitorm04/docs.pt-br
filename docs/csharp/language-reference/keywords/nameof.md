---
title: nameof (Referência de C#)
ms.date: 06/16/2017
f1_keywords:
- nameof_CSharpKeyword
- nameof
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 2695095aa4bf2035d8766f3cbcb82f4fbb290e22
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245629"
---
# <a name="nameof-c-reference"></a><span data-ttu-id="debce-102">nameof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="debce-102">nameof (C# Reference)</span></span>

<span data-ttu-id="debce-103">Usado para obter o nome de cadeia de caracteres simples (não qualificado) de uma variável, tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="debce-103">Used to obtain the simple (unqualified) string name of a variable, type, or member.</span></span>  

<span data-ttu-id="debce-104">Ao relatar erros no código, conectar links de MVC (Modelo-Exibição-Controlador), disparando eventos de propriedade alterada etc., normalmente você captura o nome da cadeia de caracteres de um método.</span><span class="sxs-lookup"><span data-stu-id="debce-104">When reporting errors in code, hooking up model-view-controller (MVC) links, firing property changed events, etc., you often want to capture the string name of a method.</span></span>  <span data-ttu-id="debce-105">Usar `nameof` ajuda a manter seu código válido ao renomear definições.</span><span class="sxs-lookup"><span data-stu-id="debce-105">Using `nameof` helps keep your code valid when renaming definitions.</span></span>  <span data-ttu-id="debce-106">Antes era necessário usar literais de cadeia de caracteres para se referir às definições, o que é frágil ao renomear os elementos de código porque as ferramentas não sabem verificar esses literais de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="debce-106">Before, you had to use string literals to refer to definitions, which is brittle when renaming code elements because tools do not know to check these string literals.</span></span>  
  
 <span data-ttu-id="debce-107">Uma expressão `nameof` tem este formato:</span><span class="sxs-lookup"><span data-stu-id="debce-107">A `nameof` expression has this form:</span></span>  
  
```csharp  
if (x == null) throw new ArgumentNullException(nameof(x));  
WriteLine(nameof(person.Address.ZipCode)); // prints "ZipCode"  
```  
  
## <a name="key-use-cases"></a><span data-ttu-id="debce-108">Principais casos de uso</span><span class="sxs-lookup"><span data-stu-id="debce-108">Key Use Cases</span></span>  
 <span data-ttu-id="debce-109">Esses exemplos mostram os principais casos de uso para `nameof`.</span><span class="sxs-lookup"><span data-stu-id="debce-109">These examples show the key use cases for `nameof`.</span></span>  
  
 <span data-ttu-id="debce-110">Validar parâmetros:</span><span class="sxs-lookup"><span data-stu-id="debce-110">Validate parameters:</span></span>  
 ```csharp  
void f(string s) {  
    if (s == null) throw new ArgumentNullException(nameof(s));  
}  
```  
  
 <span data-ttu-id="debce-111">Links de ação do MVC:</span><span class="sxs-lookup"><span data-stu-id="debce-111">MVC Action links:</span></span>  
 ```html  
<%= Html.ActionLink("Sign up",  
             @typeof(UserController),  
             @nameof(UserController.SignUp))  
%>  
```  
  
 <span data-ttu-id="debce-112">INotifyPropertyChanged:</span><span class="sxs-lookup"><span data-stu-id="debce-112">INotifyPropertyChanged:</span></span>  
 ```csharp  
int p {  
    get { return this.p; }  
    set { this.p = value; PropertyChanged(this, new PropertyChangedEventArgs(nameof(this.p)); } // nameof(p) works too  
}  
```  
  
 <span data-ttu-id="debce-113">Propriedade de dependência XAML:</span><span class="sxs-lookup"><span data-stu-id="debce-113">XAML dependency property:</span></span>  
 ```csharp  
public static DependencyProperty AgeProperty = DependencyProperty.Register(nameof(Age), typeof(int), typeof(C));  
```  
  
 <span data-ttu-id="debce-114">Registrando em log:</span><span class="sxs-lookup"><span data-stu-id="debce-114">Logging:</span></span>  
 ```csharp  
void f(int i) {  
    Log(nameof(f), "method entry");  
}  
```  
  
 <span data-ttu-id="debce-115">Atributos:</span><span class="sxs-lookup"><span data-stu-id="debce-115">Attributes:</span></span>  
 ```csharp  
[DebuggerDisplay("={" + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```  
  
## <a name="examples"></a><span data-ttu-id="debce-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="debce-116">Examples</span></span>  
 <span data-ttu-id="debce-117">Alguns exemplos de C#:</span><span class="sxs-lookup"><span data-stu-id="debce-117">Some C# examples:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="debce-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="debce-118">Remarks</span></span>  
 <span data-ttu-id="debce-119">O argumento para `nameof` deve ser um nome simples, nome qualificado, acesso de membro, acesso básico com um membro especificado ou esse acesso com um membro especificado.</span><span class="sxs-lookup"><span data-stu-id="debce-119">The argument to `nameof` must be a simple name, qualified name, member access, base access with a specified member, or this access with a specified member.</span></span>  <span data-ttu-id="debce-120">A expressão de argumento identifica uma definição de código, mas ela nunca é avaliada.</span><span class="sxs-lookup"><span data-stu-id="debce-120">The argument expression identifies a code definition, but it is never evaluated.</span></span>  
  
 <span data-ttu-id="debce-121">Como o argumento deve ser uma expressão sintaticamente, há muitas coisas não permitidas que não são úteis para a lista.</span><span class="sxs-lookup"><span data-stu-id="debce-121">Because the argument needs to be an expression syntactically, there are many things disallowed that are not useful to list.</span></span>  <span data-ttu-id="debce-122">Os itens a seguir são os que valem a pena mencionar que produzem erros: tipos predefinidos (por exemplo, `int` ou `void`), tipos que permitem valor nulo (`Point?`), tipos de matriz (`Customer[,]`), tipos de ponteiro (`Buffer*`), alias qualificado (`A::B`) e tipos genéricos não associados (`Dictionary<,>`), símbolos de pré-processamento (`DEBUG`) e rótulos (`loop:`).</span><span class="sxs-lookup"><span data-stu-id="debce-122">The following are worth mentioning that produce errors: predefined types (for example, `int` or `void`), nullable types (`Point?`), array types (`Customer[,]`), pointer types (`Buffer*`), qualified alias (`A::B`), and unbound generic types (`Dictionary<,>`), preprocessing symbols (`DEBUG`), and labels (`loop:`).</span></span>  
  
 <span data-ttu-id="debce-123">Se você precisar obter o nome totalmente qualificado, poderá usar expressão `typeof` juntamente com `nameof`.</span><span class="sxs-lookup"><span data-stu-id="debce-123">If you need to get the fully-qualified name, you can use the `typeof` expression along with `nameof`.</span></span>  <span data-ttu-id="debce-124">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="debce-124">For example:</span></span>
```csharp  
class C {
    void f(int i) {  
        Log($"{typeof(C)}.{nameof(f)}", "method entry");  
    }
}
``` 

 <span data-ttu-id="debce-125">Infelizmente `typeof` não é uma expressão de constante como `nameof`, então `typeof` não pode ser usada em conjunto com `nameof` em todos os mesmos locais como `nameof`.</span><span class="sxs-lookup"><span data-stu-id="debce-125">Unfortunately `typeof` is not a constant expression like `nameof`, so `typeof` cannot be used in conjunction with `nameof` in all the same places as `nameof`.</span></span>  <span data-ttu-id="debce-126">Por exemplo, o seguinte poderia causar um erro de compilação CS0182:</span><span class="sxs-lookup"><span data-stu-id="debce-126">For example, the following would cause a CS0182 compile error:</span></span>
 ```csharp  
[DebuggerDisplay("={" + typeof(C) + nameof(GetString) + "()}")]  
class C {  
    string GetString() { }  
}  
```    
 <span data-ttu-id="debce-127">Nos exemplos você vê que pode usar um nome de tipo e acessar um nome de método de instância.</span><span class="sxs-lookup"><span data-stu-id="debce-127">In the examples you see that you can use a type name and access an instance method name.</span></span>  <span data-ttu-id="debce-128">Você não precisa ter uma instância do tipo, como necessário nas expressões avaliadas.</span><span class="sxs-lookup"><span data-stu-id="debce-128">You do not need to have an instance of the type, as required in evaluated expressions.</span></span>  <span data-ttu-id="debce-129">Usar o nome do tipo pode ser muito conveniente em algumas situações e como você está fazendo referência ao nome e não usando os dados da instância, não precisa criar uma variável de instância ou expressão.</span><span class="sxs-lookup"><span data-stu-id="debce-129">Using the type name can be very convenient in some situations, and since you are just referring to the name and not using instance data, you do not need to contrive an instance variable or expression.</span></span>  
  
 <span data-ttu-id="debce-130">Você pode fazer referência aos membros de uma classe em expressões de atributo na classe.</span><span class="sxs-lookup"><span data-stu-id="debce-130">You can reference the members of a class in attribute expressions on the class.</span></span>  
  
 <span data-ttu-id="debce-131">Não é possível obter as informações de uma assinaturas como "`Method1 (str, str)`".</span><span class="sxs-lookup"><span data-stu-id="debce-131">There is no way to get a signatures information such as "`Method1 (str, str)`".</span></span>  <span data-ttu-id="debce-132">Uma maneira de fazer isso é usar uma expressão, `Expression e = () => A.B.Method1("s1", "s2")` e efetuar o pull de MemberInfo da árvore de expressão resultante.</span><span class="sxs-lookup"><span data-stu-id="debce-132">One way to do that is to use an Expression, `Expression e = () => A.B.Method1("s1", "s2")`, and pull the MemberInfo from the resulting expression tree.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="debce-133">Especificações da linguagem</span><span class="sxs-lookup"><span data-stu-id="debce-133">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="debce-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="debce-134">See Also</span></span>  
 [<span data-ttu-id="debce-135">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="debce-135">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="debce-136">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="debce-136">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="debce-137">typeof</span><span class="sxs-lookup"><span data-stu-id="debce-137">typeof</span></span>](../../../csharp/language-reference/keywords/typeof.md)  
 
