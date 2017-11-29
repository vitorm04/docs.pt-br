---
title: "Como converter bool? em bool com segurança (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="d6ae7-102">Como converter bool? em bool com segurança (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d6ae7-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="d6ae7-103">O tipo que permite valor nulo `bool?` pode conter três valores diferentes: `true`, `false` e `null`.</span><span class="sxs-lookup"><span data-stu-id="d6ae7-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="d6ae7-104">Portanto, o tipo `bool?` não pode ser usado em condicionais como com `if`, `for` ou `while`.</span><span class="sxs-lookup"><span data-stu-id="d6ae7-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="d6ae7-105">Por exemplo, o código a seguir gera um erro de compilador.</span><span class="sxs-lookup"><span data-stu-id="d6ae7-105">For example, the following code causes a compiler error.</span></span>  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="d6ae7-106">Isso não é permitido, porque não está claro o que `null` significa no contexto de uma condicional.</span><span class="sxs-lookup"><span data-stu-id="d6ae7-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="d6ae7-107">Para usar um `bool?` em uma instrução condicional, verifique primeiro sua propriedade <xref:System.Nullable%601.HasValue%2A> para garantir que seu valor não seja `null` e, em seguida, converta-a em `bool`.</span><span class="sxs-lookup"><span data-stu-id="d6ae7-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="d6ae7-108">Para obter mais informações, consulte [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="d6ae7-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="d6ae7-109">Se você executar a conversão em um `bool?` com um valor de `null`, uma <xref:System.InvalidOperationException> será lançada no teste condicional.</span><span class="sxs-lookup"><span data-stu-id="d6ae7-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="d6ae7-110">O exemplo a seguir mostra uma maneira de converter `bool?` em `bool` de maneira segura:</span><span class="sxs-lookup"><span data-stu-id="d6ae7-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6ae7-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d6ae7-111">Example</span></span>  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6ae7-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d6ae7-112">See Also</span></span>  
 [<span data-ttu-id="d6ae7-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d6ae7-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d6ae7-114">Palavras-chave literais</span><span class="sxs-lookup"><span data-stu-id="d6ae7-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="d6ae7-115">Tipos que permitem valor nulo</span><span class="sxs-lookup"><span data-stu-id="d6ae7-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="d6ae7-116">Operador ??</span><span class="sxs-lookup"><span data-stu-id="d6ae7-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
