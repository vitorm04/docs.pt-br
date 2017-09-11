---
title: "Como pesquisar cadeias de caracteres usando expressões regulares (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fb05d1702c75be8fd224ee0f34d7d8d3fe71f207
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a><span data-ttu-id="541a5-102">Como pesquisar cadeias de caracteres usando expressões regulares (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="541a5-102">How to: Search Strings Using Regular Expressions (C# Programming Guide)</span></span>
<span data-ttu-id="541a5-103">A classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> pode ser usada para pesquisar cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="541a5-103">The <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> class can be used to search strings.</span></span> <span data-ttu-id="541a5-104">Essas pesquisas podem variar em complexidade, de muito simples a uso pleno de expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="541a5-104">These searches can range in complexity from very simple to making full use of regular expressions.</span></span> <span data-ttu-id="541a5-105">A seguir estão dois exemplos de pesquisa de cadeia de caracteres usando a classe <xref:System.Text.RegularExpressions.Regex>.</span><span class="sxs-lookup"><span data-stu-id="541a5-105">The following are two examples of string searching by using the <xref:System.Text.RegularExpressions.Regex> class.</span></span> <span data-ttu-id="541a5-106">Para obter mais informações, consulte [Expressões regulares do .NET Framework](https://msdn.microsoft.com/library/hs600312).</span><span class="sxs-lookup"><span data-stu-id="541a5-106">For more information, see [.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312).</span></span>  
  
## <a name="example"></a><span data-ttu-id="541a5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541a5-107">Example</span></span>  
 <span data-ttu-id="541a5-108">O código a seguir é um aplicativo de console que executa uma pesquisa simples que não diferencia maiúsculas de minúsculas de cadeias de caracteres em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="541a5-108">The following code is a console application that performs a simple case-insensitive search of the strings in an array.</span></span> <span data-ttu-id="541a5-109">O método estático <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> executa a pesquisa considerando a cadeia de caracteres a pesquisar e uma cadeia de caracteres que contém o padrão de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="541a5-109">The static method <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> performs the search given the string to search and a string that contains the search pattern.</span></span> <span data-ttu-id="541a5-110">Nesse caso, um terceiro argumento é usado para indicar que o caso deve ser ignorado.</span><span class="sxs-lookup"><span data-stu-id="541a5-110">In this case, a third argument is used to indicate that case should be ignored.</span></span> <span data-ttu-id="541a5-111">Para obter mais informações, consulte <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="541a5-111">For more information, see <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="541a5-112">[!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="541a5-112">[!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="541a5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="541a5-113">Example</span></span>  
 <span data-ttu-id="541a5-114">O código a seguir é um aplicativo de console que usa expressões regulares para validar o formato de cada cadeia de caracteres em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="541a5-114">The following code is a console application that uses regular expressions to validate the format of each string in an array.</span></span> <span data-ttu-id="541a5-115">A validação requer que cada cadeia de caracteres assuma a forma de um número de telefone no qual os três grupos de dígitos são separados por traços, os dois primeiros grupos contêm três dígitos e o terceiro grupo contém quatro dígitos.</span><span class="sxs-lookup"><span data-stu-id="541a5-115">The validation requires that each string take the form of a telephone number in which three groups of digits are separated by dashes, the first two groups contain three digits, and the third group contains four digits.</span></span> <span data-ttu-id="541a5-116">Isso é feito usando a expressão regular `^\\d{3}-\\d{3}-\\d{4}$`.</span><span class="sxs-lookup"><span data-stu-id="541a5-116">This is done by using the regular expression `^\\d{3}-\\d{3}-\\d{4}$`.</span></span> <span data-ttu-id="541a5-117">Para obter mais informações, consulte [Linguagem de expressões regulares – referência rápida](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span><span class="sxs-lookup"><span data-stu-id="541a5-117">For more information, see [Regular Expression Language - Quick Reference](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).</span></span>  
  
 <span data-ttu-id="541a5-118">[!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="541a5-118">[!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="541a5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="541a5-119">See Also</span></span>  
 <span data-ttu-id="541a5-120"><xref:System.Text.RegularExpressions.Regex?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="541a5-120"><xref:System.Text.RegularExpressions.Regex?displayProperty=fullName></span></span>   
 <span data-ttu-id="541a5-121">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="541a5-121">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="541a5-122">[Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="541a5-122">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 <span data-ttu-id="541a5-123">[Expressões regulares do .NET Framework](https://msdn.microsoft.com/library/hs600312) </span><span class="sxs-lookup"><span data-stu-id="541a5-123">[.NET Framework Regular Expressions](https://msdn.microsoft.com/library/hs600312) </span></span>  
 [<span data-ttu-id="541a5-124">Linguagem de expressão regular – referência rápida</span><span class="sxs-lookup"><span data-stu-id="541a5-124">Regular Expression Language - Quick Reference</span></span>](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)

