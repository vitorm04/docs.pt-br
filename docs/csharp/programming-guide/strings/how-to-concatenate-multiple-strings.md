---
title: "Como concatenar várias cadeias de caracteres (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b191a61258a496115a4d7045046f9b4a2dbee58c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="fb2c5-102">Como concatenar várias cadeias de caracteres (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="fb2c5-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="fb2c5-103">*Concatenação* é o processo de acrescentar uma cadeia de caracteres ao final de outra cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="fb2c5-104">Ao concatenar literais ou constantes de cadeia de caracteres usando o operador `+`, o compilador cria uma única cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="fb2c5-105">A concatenação em tempo de execução não ocorre.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-105">No run time concatenation occurs.</span></span> <span data-ttu-id="fb2c5-106">No entanto, as variáveis de cadeia de caracteres podem ser concatenadas somente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="fb2c5-107">Nesse caso, é necessário entender as implicações de desempenho das várias abordagens.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb2c5-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb2c5-108">Example</span></span>  
 <span data-ttu-id="fb2c5-109">O exemplo a seguir mostra como dividir um literal de cadeia de caracteres longo em cadeias de caracteres menores, a fim de melhorar a legibilidade no código-fonte.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="fb2c5-110">Essas partes serão concatenadas em uma única cadeia de caracteres em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="fb2c5-111">Não há custos de desempenho em tempo de execução, independentemente da quantidade de cadeias de caracteres envolvidas.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 <span data-ttu-id="fb2c5-112">[!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fb2c5-112">[!code-cs[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb2c5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fb2c5-113">Example</span></span>  
 <span data-ttu-id="fb2c5-114">Para concatenar variáveis de cadeia de caracteres, você pode usar os operadores `+` ou `+=`, ou então os métodos <xref:System.String.Concat%2A?displayProperty=fullName>, <xref:System.String.Format%2A?displayProperty=fullName> ou <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-114">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=fullName>, <xref:System.String.Format%2A?displayProperty=fullName> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=fullName> methods.</span></span> <span data-ttu-id="fb2c5-115">O operador `+` é fácil de usar e torna o código intuitivo.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-115">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="fb2c5-116">Mesmo ao usar vários operadores + em uma instrução, o conteúdo da cadeia de caracteres será copiada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-116">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="fb2c5-117">Porém, se essa operação for repetida várias vezes, por exemplo, em um loop, problemas de eficiência poderão ocorrer.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-117">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="fb2c5-118">Por exemplo, observe o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="fb2c5-118">For example, note the following code:</span></span>  
  
 <span data-ttu-id="fb2c5-119">[!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="fb2c5-119">[!code-cs[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb2c5-120">Em operações de concatenação de cadeia de caracteres, o compilador C# trata uma cadeia de caracteres nula da mesma maneira que uma cadeia de caracteres vazia, mas não converte o valor da cadeia de caracteres nula original.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-120">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="fb2c5-121">Se você não estiver concatenando grandes quantidades de cadeias de caracteres (por exemplo, em um loop), o custo de desempenho provavelmente não será significativo.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-121">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="fb2c5-122">O mesmo é verdadeiro para os métodos <xref:System.String.Concat%2A?displayProperty=fullName> e <xref:System.String.Format%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-122">The same is true for the <xref:System.String.Concat%2A?displayProperty=fullName> and <xref:System.String.Format%2A?displayProperty=fullName> methods.</span></span>  
  
 <span data-ttu-id="fb2c5-123">No entanto, quando o desempenho for importante, sempre use a classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-123">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="fb2c5-124">O código a seguir usa o método <xref:System.Text.StringBuilder.Append%2A> da classe <xref:System.Text.StringBuilder> para concatenar cadeias de caracteres sem o efeito de encadeamento do operador `+`.</span><span class="sxs-lookup"><span data-stu-id="fb2c5-124">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 <span data-ttu-id="fb2c5-125">[!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="fb2c5-125">[!code-cs[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb2c5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb2c5-126">See Also</span></span>  
 <span data-ttu-id="fb2c5-127"><xref:System.String></span><span class="sxs-lookup"><span data-stu-id="fb2c5-127"><xref:System.String></span></span>   
 <span data-ttu-id="fb2c5-128"><xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="fb2c5-128"><xref:System.Text.StringBuilder></span></span>   
 <span data-ttu-id="fb2c5-129">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb2c5-129">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="fb2c5-130">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="fb2c5-130">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

