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
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c0ef96f1cb074c32208457c192d53c69d95a102d
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a>Como analisar cadeias de caracteres usando String.Split (Guia de Programação em C#)
O exemplo de código a seguir demonstra como uma cadeia de caracteres pode ser analisada usando o método <xref:System.String.Split%2A?displayProperty=fullName>. Como entrada, <xref:System.String.Split%2A> obtém uma matriz de caracteres que indica quais caracteres separam subcadeias de caracteres interessantes da cadeia de caracteres de destino.  A função retorna uma matriz das subcadeias de caracteres.  
  
 Este exemplo utiliza espaços, vírgulas, pontos, dois-pontos e tabulações, todos passados em uma matriz que contém esses caracteres de separação para <xref:System.String.Split%2A>.  Cada palavra na frase da cadeia de caracteres de destino será exibida separadamente da matriz de cadeias de caracteres resultante.  
  
## <a name="example"></a>Exemplo  
 [!code-cs[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a>Exemplo  
 Por padrão, String.Split retorna cadeias de caracteres vazias quando dois caracteres de separação aparecem contiguamente na cadeia de caracteres de destino.  É possível passar um parâmetro opcional StringSplitOptions.RemoveEmptyEntries para excluir cadeias de caracteres vazias na saída.  
  
 String.Split pode obter uma matriz de cadeias de caracteres (sequências de caracteres que atuam como separadores para analisar a cadeia de caracteres de destino, em vez de um único caractere).  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)   
 [Expressões regulares do .NET Framework](https://msdn.microsoft.com/library/hs600312)

