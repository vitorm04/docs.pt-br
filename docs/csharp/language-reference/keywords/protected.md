---
title: protected (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 2da8211ac21a5016478e7b881e7f2f9925b49cef
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001328"
---
# <a name="protected-c-reference"></a><span data-ttu-id="740b5-102">protected (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="740b5-102">protected (C# Reference)</span></span>
<span data-ttu-id="740b5-103">A palavra-chave `protected` é um modificador de acesso de membro.</span><span class="sxs-lookup"><span data-stu-id="740b5-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="740b5-104">Esta página aborda o acesso `protected`.</span><span class="sxs-lookup"><span data-stu-id="740b5-104">This page covers `protected` access.</span></span> <span data-ttu-id="740b5-105">A palavra-chave `protected` também faz parte dos modificadores de acesso [`protected internal`](./protected-internal.md) e [`private protected`](./private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="740b5-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="740b5-106">Um membro protegido é acessível dentro de sua classe e por instâncias da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="740b5-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="740b5-107">Para obter uma comparação de `protected` com os outros modificadores de acesso, consulte [Níveis de acessibilidade](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="740b5-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="740b5-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="740b5-108">Example</span></span>  
 <span data-ttu-id="740b5-109">Um membro protegido de uma classe base será acessível em uma classe derivada somente se o acesso ocorrer por meio do tipo da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="740b5-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="740b5-110">Por exemplo, considere o seguinte segmento de código:</span><span class="sxs-lookup"><span data-stu-id="740b5-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="740b5-111">A instrução `a.x = 10` gera um erro porque ela é feita dentro do método estático Main e não em uma instância da classe B.</span><span class="sxs-lookup"><span data-stu-id="740b5-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="740b5-112">Membros de struct não podem ser protegidos porque o struct não pode ser herdado.</span><span class="sxs-lookup"><span data-stu-id="740b5-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="740b5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="740b5-113">Example</span></span>  
 <span data-ttu-id="740b5-114">Nesse exemplo, a classe `DerivedPoint` é derivada de `Point`.</span><span class="sxs-lookup"><span data-stu-id="740b5-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="740b5-115">Portanto, você pode acessar os membros protegidos da classe base diretamente da classe derivada.</span><span class="sxs-lookup"><span data-stu-id="740b5-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="740b5-116">Se você alterar os níveis de acesso de `x` e `y` para [private](../../../csharp/language-reference/keywords/private.md), o compilador emitirá as mensagens de erro:</span><span class="sxs-lookup"><span data-stu-id="740b5-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="740b5-117">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="740b5-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## 

- [<span data-ttu-id="740b5-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="740b5-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="740b5-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="740b5-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="740b5-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="740b5-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="740b5-121">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="740b5-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="740b5-122">Níveis de acessibilidade</span><span class="sxs-lookup"><span data-stu-id="740b5-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="740b5-123">Modificadores</span><span class="sxs-lookup"><span data-stu-id="740b5-123">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="740b5-124">public</span><span class="sxs-lookup"><span data-stu-id="740b5-124">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="740b5-125">private</span><span class="sxs-lookup"><span data-stu-id="740b5-125">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="740b5-126">internal</span><span class="sxs-lookup"><span data-stu-id="740b5-126">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
- <span data-ttu-id="740b5-127">[Questões de segurança de palavras-chave virtuais internas](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="740b5-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>