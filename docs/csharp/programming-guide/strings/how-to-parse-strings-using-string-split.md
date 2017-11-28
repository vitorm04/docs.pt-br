---
title: "Como analisar cadeias de caracteres usando String.Split (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a><span data-ttu-id="3bc0e-102">Como analisar cadeias de caracteres usando String.Split (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="3bc0e-102">How to: Parse Strings Using String.Split (C# Programming Guide)</span></span>
<span data-ttu-id="3bc0e-103">O exemplo de código a seguir demonstra como uma cadeia de caracteres pode ser analisada usando o método <xref:System.String.Split%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-103">The following code example demonstrates how a string can be parsed using the <xref:System.String.Split%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="3bc0e-104">Como entrada, <xref:System.String.Split%2A> obtém uma matriz de caracteres que indica quais caracteres separam subcadeias de caracteres interessantes da cadeia de caracteres de destino.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-104">As input, <xref:System.String.Split%2A> takes an array of characters that indicate which characters separate interesting sub strings of the target string.</span></span>  <span data-ttu-id="3bc0e-105">A função retorna uma matriz das subcadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-105">The function returns an array of the sub strings.</span></span>  
  
 <span data-ttu-id="3bc0e-106">Este exemplo utiliza espaços, vírgulas, pontos, dois-pontos e tabulações, todos passados em uma matriz que contém esses caracteres de separação para <xref:System.String.Split%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-106">This example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters to <xref:System.String.Split%2A>.</span></span>  <span data-ttu-id="3bc0e-107">Cada palavra na frase da cadeia de caracteres de destino será exibida separadamente da matriz de cadeias de caracteres resultante.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-107">Each word in the target string's sentence displays separately from the resulting array of strings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3bc0e-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bc0e-108">Example</span></span>  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="3bc0e-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3bc0e-109">Example</span></span>  
 <span data-ttu-id="3bc0e-110">Por padrão, String.Split retorna cadeias de caracteres vazias quando dois caracteres de separação aparecem contiguamente na cadeia de caracteres de destino.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-110">By default, String.Split returns empty strings when two separating characters appear contiguously in the target string.</span></span>  <span data-ttu-id="3bc0e-111">É possível passar um parâmetro opcional StringSplitOptions.RemoveEmptyEntries para excluir cadeias de caracteres vazias na saída.</span><span class="sxs-lookup"><span data-stu-id="3bc0e-111">You can pass an optional StringSplitOptions.RemoveEmptyEntries parameter to exclude any empty strings in the output.</span></span>  
  
 <span data-ttu-id="3bc0e-112">String.Split pode obter uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).</span><span class="sxs-lookup"><span data-stu-id="3bc0e-112">String.Split can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3bc0e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3bc0e-113">See Also</span></span>  
 [<span data-ttu-id="3bc0e-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3bc0e-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3bc0e-115">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="3bc0e-115">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)  
 [<span data-ttu-id="3bc0e-116">Expressões regulares do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3bc0e-116">.NET Framework Regular Expressions</span></span>](https://msdn.microsoft.com/library/hs600312)
