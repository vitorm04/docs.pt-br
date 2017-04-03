---
title: "Como Converter entre Codificações Herdadas e Unicode (Guia de Programação em C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee93b20c0e57df42f0e1fba2aaf0688ae58cae06
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a>Como converter entre codificações herdadas e Unicode (Guia de Programação em C#)
No C#, todas as cadeias de caracteres na memória são codificadas como Unicode (UTF-16). Ao colocar dados do armazenamento em um objeto `string`, esses dados são automaticamente convertidos para UTF-16. Se os dados contiverem apenas valores ASCII de 0 a 127, a conversão não exigirá nenhum esforço a mais de sua parte. No entanto, se o texto de origem contiver valores de byte ASCII estendidos (de 128 a 255), os caracteres estendidos serão interpretados por padrão, de acordo com a página de código atual. Para especificar que o texto de origem deve ser interpretado de acordo com uma página de código diferente, use a classe <xref:System.Text.Encoding?displayProperty=fullName>, conforme mostrado no exemplo a seguir.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como converter um arquivo de texto codificado em ASCII de 8 bits, interpretando o texto de origem de acordo com a Página de Código 737 do Windows.  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## <a name="see-also"></a>Consulte também  
 [Cadeias de Caracteres](../../../csharp/programming-guide/strings/index.md)
