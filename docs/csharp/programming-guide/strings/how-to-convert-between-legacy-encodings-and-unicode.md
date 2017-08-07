---
title: "Como converter entre codificações herdadas e Unicode (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], legacy to unicode encoding
- strings [C#], converting between encodings
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
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
ms.openlocfilehash: a016f4ab7de25eec408243cb9b467f9255556bba
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a>Como converter entre codificações herdadas e Unicode (Guia de Programação em C#)
No C#, todas as cadeias de caracteres na memória são codificadas como Unicode (UTF-16). Ao colocar dados do armazenamento em um objeto `string`, esses dados são automaticamente convertidos para UTF-16. Se os dados contiverem apenas valores ASCII de 0 a 127, a conversão não exigirá nenhum esforço a mais de sua parte. No entanto, se o texto de origem contiver valores de byte ASCII estendidos (de 128 a 255), os caracteres estendidos serão interpretados por padrão, de acordo com a página de código atual. Para especificar que o texto de origem deve ser interpretado de acordo com uma página de código diferente, use a classe <xref:System.Text.Encoding?displayProperty=fullName>, conforme mostrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como converter um arquivo de texto codificado em ASCII de 8 bits, interpretando o texto de origem de acordo com a Página de Código 737 do Windows.  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)

