---
title: internal – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- internal_CSharpKeyword
- internal
helpviewer_keywords:
- internal keyword [C#]
ms.assetid: 6ee0785c-d7c8-49b8-bb72-0a4dfbcb6461
ms.openlocfilehash: f72866cafbf291310d88fc6f18a5a15dc77c621d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422721"
---
# <a name="internal-c-reference"></a><span data-ttu-id="b8dcb-102">internal (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b8dcb-102">internal (C# Reference)</span></span>
<span data-ttu-id="b8dcb-103">A palavra-chave `internal` é um [modificador de acesso](./access-modifiers.md) para tipos e membros de tipo.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-103">The `internal` keyword is an [access modifier](./access-modifiers.md) for types and type members.</span></span> 
  
 > <span data-ttu-id="b8dcb-104">Esta página aborda o acesso `internal`.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-104">This page covers `internal` access.</span></span> <span data-ttu-id="b8dcb-105">A palavra-chave `internal` também faz parte do modificador de acesso [`protected internal`](./protected-internal.md).</span><span class="sxs-lookup"><span data-stu-id="b8dcb-105">The `internal` keyword is also part of the [`protected internal`](./protected-internal.md) access modifier.</span></span>
  
<span data-ttu-id="b8dcb-106">Tipos ou membros internos são acessíveis somente em arquivos no mesmo assembly, como neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="b8dcb-106">Internal types or members are accessible only within files in the same assembly, as in this example:</span></span>  
  
```csharp  
public class BaseClass   
{  
    // Only accessible within the same assembly.
    internal static int x = 0;
}  
```  

 <span data-ttu-id="b8dcb-107">Para obter uma comparação de `internal` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](./accessibility-levels.md) e [Modificadores de acesso](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="b8dcb-107">For a comparison of `internal` with the other access modifiers, see [Accessibility Levels](./accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="b8dcb-108">Para saber mais sobre assemblies, confira [Assembly no .NET](../../../standard/assembly/index.md).</span><span class="sxs-lookup"><span data-stu-id="b8dcb-108">For more information about assemblies, see [Assemblies in .NET](../../../standard/assembly/index.md).</span></span>  
  
 <span data-ttu-id="b8dcb-109">Um uso comum do acesso interno é no desenvolvimento baseado em componente, porque ele permite que um grupo de componentes colabore de maneira particular, sem serem expostos para o restante do código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-109">A common use of internal access is in component-based development because it enables a group of components to cooperate in a private manner without being exposed to the rest of the application code.</span></span> <span data-ttu-id="b8dcb-110">Por exemplo, uma estrutura para a criação de interfaces gráficas do usuário pode fornecer as classes `Control` e `Form`, que cooperam através do uso de membros com acesso interno.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-110">For example, a framework for building graphical user interfaces could provide `Control` and `Form` classes that cooperate by using members with internal access.</span></span> <span data-ttu-id="b8dcb-111">Uma vez que esses membros são internos, eles não são expostos ao código que está usando a estrutura.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-111">Since these members are internal, they are not exposed to code that is using the framework.</span></span>  
  
 <span data-ttu-id="b8dcb-112">É um erro fazer referência a um tipo ou um membro com acesso interno fora do assembly no qual ele foi definido.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-112">It is an error to reference a type or a member with internal access outside the assembly within which it was defined.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8dcb-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8dcb-113">Example</span></span>  
 <span data-ttu-id="b8dcb-114">Este exemplo contém dois arquivos, `Assembly1.cs` e `Assembly1_a.cs`.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-114">This example contains two files, `Assembly1.cs` and `Assembly1_a.cs`.</span></span> <span data-ttu-id="b8dcb-115">O primeiro arquivo contém uma classe base interna `BaseClass`.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-115">The first file contains an internal base class, `BaseClass`.</span></span> <span data-ttu-id="b8dcb-116">No segundo arquivo, uma tentativa de instanciar a `BaseClass` produzirá um erro.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-116">In the second file, an attempt to instantiate `BaseClass` will produce an error.</span></span>  
  
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
      var myBase = new BaseClass();   // CS0122  
   }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="b8dcb-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8dcb-117">Example</span></span>  
 <span data-ttu-id="b8dcb-118">Neste exemplo, use os mesmos arquivos que você usou no exemplo 1 e altere o nível de acessibilidade da `BaseClass` para `public`.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-118">In this example, use the same files you used in example 1, and change the accessibility level of `BaseClass` to `public`.</span></span> <span data-ttu-id="b8dcb-119">Também altere o nível de acessibilidade do membro `intM` para `internal`.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-119">Also change the accessibility level of the member `intM` to `internal`.</span></span> <span data-ttu-id="b8dcb-120">Nesse caso, você pode instanciar a classe, mas não pode acessar o membro interno.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-120">In this case, you can instantiate the class, but you cannot access the internal member.</span></span>  
  
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
// Compile with: /reference:Assembly2.dll  
public class TestAccess   
{  
   static void Main()   
   {  
      var myBase = new BaseClass();   // Ok.  
      BaseClass.intM = 444;    // CS0117  
   }  
}  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="b8dcb-121">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="b8dcb-121">C# Language Specification</span></span>  

<span data-ttu-id="b8dcb-122">Para obter mais informações, veja [Acessibilidade declarada](~/_csharplang/spec/basic-concepts.md#declared-accessibility) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="b8dcb-122">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="b8dcb-123">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="b8dcb-123">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b8dcb-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8dcb-124">See also</span></span>

- [<span data-ttu-id="b8dcb-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b8dcb-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b8dcb-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b8dcb-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b8dcb-127">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="b8dcb-127">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b8dcb-128">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="b8dcb-128">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="b8dcb-129">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="b8dcb-129">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="b8dcb-130">Modificadores</span><span class="sxs-lookup"><span data-stu-id="b8dcb-130">Modifiers</span></span>](index.md)
- [<span data-ttu-id="b8dcb-131">public</span><span class="sxs-lookup"><span data-stu-id="b8dcb-131">public</span></span>](./public.md)
- [<span data-ttu-id="b8dcb-132">private</span><span class="sxs-lookup"><span data-stu-id="b8dcb-132">private</span></span>](./private.md)
- [<span data-ttu-id="b8dcb-133">protected</span><span class="sxs-lookup"><span data-stu-id="b8dcb-133">protected</span></span>](./protected.md)
