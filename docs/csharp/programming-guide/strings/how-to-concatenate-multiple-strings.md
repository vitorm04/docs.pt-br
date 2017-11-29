---
title: "Como concatenar várias cadeias de caracteres (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="722ad-102">Como concatenar várias cadeias de caracteres (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="722ad-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="722ad-103">*Concatenação* é o processo de acrescentar uma cadeia de caracteres ao final de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="722ad-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="722ad-104">Ao concatenar literais ou constantes de cadeia de caracteres usando o operador `+`, o compilador cria uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="722ad-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="722ad-105">A concatenação em tempo de execução não ocorre.</span><span class="sxs-lookup"><span data-stu-id="722ad-105">No run time concatenation occurs.</span></span> <span data-ttu-id="722ad-106">No entanto, as variáveis de cadeia de caracteres podem ser concatenadas somente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="722ad-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="722ad-107">Nesse caso, é necessário entender as implicações de desempenho das várias abordagens.</span><span class="sxs-lookup"><span data-stu-id="722ad-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="722ad-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="722ad-108">Example</span></span>  
 <span data-ttu-id="722ad-109">O exemplo a seguir mostra como dividir um literal de cadeia de caracteres longo em cadeias de caracteres menores, a fim de melhorar a legibilidade no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="722ad-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="722ad-110">Essas partes serão concatenadas em uma única cadeia de caracteres em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="722ad-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="722ad-111">Não há custos de desempenho em tempo de execução, independentemente da quantidade de cadeias de caracteres envolvidas.</span><span class="sxs-lookup"><span data-stu-id="722ad-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="722ad-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="722ad-112">Example</span></span>  
 <span data-ttu-id="722ad-113">Para concatenar variáveis de cadeia de caracteres, você pode usar os operadores `+` ou `+=`, ou então os métodos <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="722ad-113">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="722ad-114">O operador `+` é fácil de usar e torna o código intuitivo.</span><span class="sxs-lookup"><span data-stu-id="722ad-114">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="722ad-115">Mesmo ao usar vários operadores + em uma instrução, o conteúdo da cadeia de caracteres será copiada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="722ad-115">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="722ad-116">Porém, se essa operação for repetida várias vezes, por exemplo, em um loop, problemas de eficiência poderão ocorrer.</span><span class="sxs-lookup"><span data-stu-id="722ad-116">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="722ad-117">Por exemplo, observe o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="722ad-117">For example, note the following code:</span></span>  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="722ad-118">Em operações de concatenação de cadeia de caracteres, o compilador C# trata uma cadeia de caracteres nula da mesma maneira que uma cadeia de caracteres vazia, mas não converte o valor da cadeia de caracteres nula original.</span><span class="sxs-lookup"><span data-stu-id="722ad-118">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="722ad-119">Se você não estiver concatenando grandes quantidades de cadeias de caracteres (por exemplo, em um loop), o custo de desempenho provavelmente não será significativo.</span><span class="sxs-lookup"><span data-stu-id="722ad-119">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="722ad-120">O mesmo é verdadeiro para os métodos <xref:System.String.Concat%2A?displayProperty=nameWithType> e <xref:System.String.Format%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="722ad-120">The same is true for the <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType> methods.</span></span>  
  
 <span data-ttu-id="722ad-121">No entanto, quando o desempenho for importante, sempre use a classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="722ad-121">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="722ad-122">O código a seguir usa o método <xref:System.Text.StringBuilder.Append%2A> da classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres sem o efeito de encadeamento do operador `+`.</span><span class="sxs-lookup"><span data-stu-id="722ad-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="722ad-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="722ad-123">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="722ad-124">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="722ad-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="722ad-125">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="722ad-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
