---
title: internal (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: d2fcc19bb7bc6de373412e7728f3025647c0435d
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961476"
---
# <a name="internal-c-reference"></a><span data-ttu-id="83347-102">internal (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="83347-102">internal (C# Reference)</span></span>
<span data-ttu-id="83347-103">A palavra-chave `internal` é um [modificador de acesso](../../../csharp/language-reference/keywords/access-modifiers.md) para tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="83347-103">The `internal` keyword is an [access modifier](../../../csharp/language-reference/keywords/access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="83347-104">Esta página aborda o acesso `internal`.</span><span class="sxs-lookup"><span data-stu-id="83347-104">This page covers `internal` access.</span></span> <span data-ttu-id="83347-105">A palavra-chave `internal` também faz parte do modificador de acesso [`protected internal`](./protected-internal.md).</span><span class="sxs-lookup"><span data-stu-id="83347-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="83347-106">Tipos ou membros internos são acessíveis somente em arquivos no mesmo assembly, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="83347-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly  
    internal static int x = 0;  
}  
```  

 <span data-ttu-id="83347-107">Para obter uma comparação de `internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md) e [Modificadores de acesso](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="83347-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="83347-108">Para obter mais informações sobre assemblies, consulte [Assemblies e o cache de assembly global](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span><span class="sxs-lookup"><span data-stu-id="83347-108">For more information about assemblies, see [Assemblies and the Global Assembly Cache](../../../csharp/programming-guide/concepts/assemblies-gac/index.md).</span></span>  
  
 <span data-ttu-id="83347-109">Um uso comum do acesso interno é no desenvolvimento baseado em componente, porque ele permite que um grupo de componentes colabore de maneira particular, sem serem expostos para o restante do código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="83347-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="83347-110">Por exemplo, uma estrutura para a criação de interfaces gráficas do usuário pode fornecer as classes `Control` e `Form`, que cooperam através do uso de membros com acesso interno.</span><span class="sxs-lookup"><span data-stu-id="83347-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="83347-111">Uma vez que esses membros são internos, eles não são expostos ao código que está usando a estrutura.</span><span class="sxs-lookup"><span data-stu-id="83347-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="83347-112">É um erro fazer referência a um tipo ou um membro com acesso interno fora do assembly no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="83347-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="83347-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83347-113">Example</span></span>  
 <span data-ttu-id="83347-114">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="83347-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="83347-115">O primeiro arquivo contém uma classe base interna `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="83347-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="83347-116">No segundo arquivo, uma tentativa de instanciar a `BaseClass` produzirá um erro.</span><span class="sxs-lookup"><span data-stu-id="83347-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
```csharp  
// Assembly1.cs  
// Compile with: /target:library  
internal class BaseClass   
{  
   public static int intM = 0;  
}  
```  
  
```csharp  
// Assembly1_a.cs  
// Compile with: /reference:Assembly1.dll  
class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="83347-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="83347-117">Example</span></span>  
 <span data-ttu-id="83347-118">Neste exemplo, use os mesmos arquivos que você usou no exemplo 1 e altere o nível de acessibilidade da `BaseClass` para `public`.</span><span class="sxs-lookup"><span data-stu-id="83347-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="83347-119">Também altere o nível de acessibilidade do membro `IntM` para `internal`.</span><span class="sxs-lookup"><span data-stu-id="83347-119">Also change the accessibility level of the member `IntM` to `internal`.</span></span> <span data-ttu-id="83347-120">Nesse caso, você pode instanciar a classe, mas não pode acessar o membro interno.</span><span class="sxs-lookup"><span data-stu-id="83347-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
```csharp  
// Assembly2.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   internal static int intM = 0;  
}  
```  
  
```csharp  
// Assembly2_a.cs  
// Compile with: /reference:Assembly1.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      BaseClass myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="83347-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="83347-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="83347-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83347-122">See Also</span></span>  
 [<span data-ttu-id="83347-123">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="83347-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="83347-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="83347-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="83347-125">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="83347-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="83347-126">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="83347-126">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="83347-127">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="83347-127">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="83347-128">Modificadores</span><span class="sxs-lookup"><span data-stu-id="83347-128">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="83347-129">public</span><span class="sxs-lookup"><span data-stu-id="83347-129">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="83347-130">private</span><span class="sxs-lookup"><span data-stu-id="83347-130">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="83347-131">protected</span><span class="sxs-lookup"><span data-stu-id="83347-131">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
