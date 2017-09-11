---
title: "Como analisar cadeias de caracteres usando String.Split (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: 17
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
ms.sourcegitcommit: d74c1d0760d4e776c2cf4c7dea1dac060c85a83c
ms.openlocfilehash: e25dbf6b86c82808622377c0618cd956541c6e09
ms.contentlocale: pt-br
ms.lasthandoff: 09/05/2017

---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="78a2f-102">Como analisar cadeias de caracteres usando String.Split (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="78a2f-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="78a2f-103">O exemplo de código a seguir demonstra como uma cadeia de caracteres pode ser analisada usando o método <xref:System.String.Split%2A?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="78a2f-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="78a2f-104">Como entrada, <xref:System.String.Split%2A> obtém uma matriz de caracteres que indica quais caracteres separam subcadeias de caracteres interessantes da cadeia de caracteres de destino.</span><span class="sxs-lookup"><span data-stu-id="78a2f-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="78a2f-105">A função retorna uma matriz das subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="78a2f-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="78a2f-106">Este exemplo utiliza espaços, vírgulas, pontos, dois-pontos e tabulações, todos passados em uma matriz que contém esses caracteres de separação para <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="78a2f-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="78a2f-107">Cada palavra na frase da cadeia de caracteres de destino será exibida separadamente da matriz de cadeias de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="78a2f-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a2f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78a2f-108">Example</span></span>  
 <span data-ttu-id="78a2f-109">[!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="78a2f-109">[!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="78a2f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78a2f-110">Example</span></span>  
 <span data-ttu-id="78a2f-111">Por padrão, String.Split retorna cadeias de caracteres vazias quando dois caracteres de separação aparecem contiguamente na cadeia de caracteres de destino.</span><span class="sxs-lookup"><span data-stu-id="78a2f-111">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="78a2f-112">É possível passar um parâmetro opcional StringSplitOptions.RemoveEmptyEntries para excluir cadeias de caracteres vazias na saída.</span><span class="sxs-lookup"><span data-stu-id="78a2f-112">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="78a2f-113">String.Split pode obter uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).</span><span class="sxs-lookup"><span data-stu-id="78a2f-113">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a><span data-ttu-id="78a2f-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78a2f-114">See Also</span></span>  
 <span data-ttu-id="78a2f-115">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="78a2f-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="78a2f-116">[Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md) </span><span class="sxs-lookup"><span data-stu-id="78a2f-116">[Strings](../../../csharp/programming-guide/strings/index.md) </span></span>  
 [<span data-ttu-id="78a2f-117">Expressões regulares do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="78a2f-117">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)

