---
title: "Como pesquisar cadeias de caracteres usando expressões regulares (Guia de Programação em C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 13342f5b6a3b236170ce4fa6c70492d9427b77c3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a>Como pesquisar cadeias de caracteres usando expressões regulares (Guia de Programação em C#)
A classe <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName> pode ser usada para pesquisar cadeias de caracteres. Essas pesquisas podem variar em complexidade, de muito simples a uso pleno de expressões regulares. A seguir, há dois exemplos de pesquisa de cadeia de caracteres usando a classe <xref:System.Text.RegularExpressions.Regex>. Para obter mais informações, consulte [Expressões regulares do .NET Framework](https://msdn.microsoft.com/library/hs600312).  
  
## <a name="example"></a>Exemplo  
 O código a seguir é um aplicativo de console que executa uma pesquisa simples que não diferencia maiúsculas de minúsculas de cadeias de caracteres em uma matriz. O método estático <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=fullName> executa a pesquisa tendo em conta a cadeia de caracteres a ser pesquisada e uma cadeia de caracteres que contém o padrão de pesquisa. Nesse caso, um terceiro argumento é usado para indicar que o caso deve ser ignorado. Para obter mais informações, consulte <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=fullName>.  
  
 [!code-cs[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a>Exemplo  
 O código a seguir é um aplicativo de console que usa expressões regulares para validar o formato de cada cadeia de caracteres em uma matriz. A validação requer que cada cadeia de caracteres assuma a forma de um número de telefone no qual os três grupos de dígitos são separados por traços, os dois primeiros grupos contêm três dígitos e o terceiro grupo contém quatro dígitos. Isso é feito usando a expressão regular `^\\d{3}-\\d{3}-\\d{4}$`. Para obter mais informações, consulte [Linguagem de expressões regulares – referência rápida](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).  
  
 [!code-cs[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=fullName>   
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)   
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)   
 [Expressões regulares do .NET Framework](https://msdn.microsoft.com/library/hs600312)   
 [Linguagem de expressão regular – referência rápida](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
