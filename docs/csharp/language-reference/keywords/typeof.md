---
title: typeof (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- typeof
- typeof_CSharpKeyword
helpviewer_keywords:
- typeof keyword [C#]
ms.assetid: 0c08d880-515e-46bb-8cd2-48b8dd62c08d
ms.openlocfilehash: 4203b597d7045a13ffed9e61ddbbde57e2113c23
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2018
---
# <a name="typeof-c-reference"></a><span data-ttu-id="7cc94-102">typeof (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7cc94-102">typeof (C# Reference)</span></span>
<span data-ttu-id="7cc94-103">Usado para obter o objeto `System.Type` para um tipo.</span><span class="sxs-lookup"><span data-stu-id="7cc94-103">Used to obtain the `System.Type` object for a type.</span></span> <span data-ttu-id="7cc94-104">Uma expressão `typeof` usa o seguinte formato:</span><span class="sxs-lookup"><span data-stu-id="7cc94-104">A `typeof` expression takes the following form:</span></span>  
  
```csharp  
System.Type type = typeof(int);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7cc94-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7cc94-105">Remarks</span></span>  
 <span data-ttu-id="7cc94-106">Para obter o tipo de tempo de execução de uma expressão, você pode usar o método do .NET Framework <xref:System.Object.GetType%2A>, assim como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7cc94-106">To obtain the run-time type of an expression, you can use the .NET Framework method <xref:System.Object.GetType%2A>, as in the following example:</span></span>  
  
```csharp  
int i = 0;  
System.Type type = i.GetType();  
```  
  
 <span data-ttu-id="7cc94-107">O operador `typeof` não pode ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="7cc94-107">The `typeof` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="7cc94-108">O operador `typeof` também pode ser usado em tipos genéricos abertos.</span><span class="sxs-lookup"><span data-stu-id="7cc94-108">The `typeof` operator can also be used on open generic types.</span></span> <span data-ttu-id="7cc94-109">Tipos com mais de um parâmetro de tipo devem ter o número apropriado de vírgulas na especificação.</span><span class="sxs-lookup"><span data-stu-id="7cc94-109">Types with more than one type parameter must have the appropriate number of commas in the specification.</span></span> <span data-ttu-id="7cc94-110">O exemplo a seguir mostra como determinar se o tipo de retorno de um método é um <xref:System.Collections.Generic.IEnumerable%601> genérico.</span><span class="sxs-lookup"><span data-stu-id="7cc94-110">The following example shows how to determine whether the return type of a method is a generic <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="7cc94-111">Suponha que o método seja uma instância de um tipo de MethodInfo:</span><span class="sxs-lookup"><span data-stu-id="7cc94-111">Assume that method is an instance of a MethodInfo type:</span></span>  
  
```csharp  
string s = method.ReturnType.GetInterface  
    (typeof(System.Collections.Generic.IEnumerable<>).FullName);  
```  
  
## <a name="example"></a><span data-ttu-id="7cc94-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7cc94-112">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="7cc94-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7cc94-113">Example</span></span>  
 <span data-ttu-id="7cc94-114">Este exemplo usa o método <xref:System.Object.GetType%2A> para determinar o tipo que é usado para conter o resultado de um cálculo numérico.</span><span class="sxs-lookup"><span data-stu-id="7cc94-114">This sample uses the <xref:System.Object.GetType%2A> method to determine the type that is used to contain the result of a numeric calculation.</span></span> <span data-ttu-id="7cc94-115">Isso depende dos requisitos de armazenamento do número resultante.</span><span class="sxs-lookup"><span data-stu-id="7cc94-115">This depends on the storage requirements of the resulting number.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/typeof_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7cc94-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7cc94-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7cc94-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cc94-117">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 [<span data-ttu-id="7cc94-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="7cc94-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7cc94-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="7cc94-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7cc94-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="7cc94-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7cc94-121">is</span><span class="sxs-lookup"><span data-stu-id="7cc94-121">is</span></span>](../../../csharp/language-reference/keywords/is.md)  
 [<span data-ttu-id="7cc94-122">Palavras-chave do operador</span><span class="sxs-lookup"><span data-stu-id="7cc94-122">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)
