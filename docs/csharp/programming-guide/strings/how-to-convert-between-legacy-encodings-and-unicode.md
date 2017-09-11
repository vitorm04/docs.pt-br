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
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a><span data-ttu-id="f3fc2-102">Como converter entre codificações herdadas e Unicode (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="f3fc2-102">How to: Convert Between Legacy Encodings and Unicode (C# Programming Guide)</span></span>
<span data-ttu-id="f3fc2-103">No C#, todas as cadeias de caracteres na memória são codificadas como Unicode (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="f3fc2-103">In C#, all strings in memory are encoded as Unicode (UTF-16).</span></span> <span data-ttu-id="f3fc2-104">Ao colocar dados do armazenamento em um objeto `string`, esses dados são automaticamente convertidos para UTF-16.</span><span class="sxs-lookup"><span data-stu-id="f3fc2-104">When you bring data from storage into a `string` object, the data is automatically converted to UTF-16.</span></span> <span data-ttu-id="f3fc2-105">Se os dados contiverem apenas valores ASCII de 0 a 127, a conversão não exigirá nenhum esforço a mais de sua parte.</span><span class="sxs-lookup"><span data-stu-id="f3fc2-105">If the data contains only ASCII values from 0 through 127, the conversion requires no extra effort on your part.</span></span> <span data-ttu-id="f3fc2-106">No entanto, se o texto de origem contiver valores de byte ASCII estendidos (de 128 a 255), os caracteres estendidos serão interpretados por padrão, de acordo com a página de código atual.</span><span class="sxs-lookup"><span data-stu-id="f3fc2-106">However, if the source text contains extended ASCII byte values (128 through 255), the extended characters will be interpreted by default according to the current code page.</span></span> <span data-ttu-id="f3fc2-107">Para especificar que o texto de origem deve ser interpretado de acordo com uma página de código diferente, use a classe <xref:System.Text.Encoding?displayProperty=fullName>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f3fc2-107">To specify that the source text should be interpreted according to a different code page, use the <xref:System.Text.Encoding?displayProperty=fullName> class as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3fc2-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3fc2-108">Example</span></span>  
 <span data-ttu-id="f3fc2-109">O exemplo a seguir mostra como converter um arquivo de texto codificado em ASCII de 8 bits, interpretando o texto de origem de acordo com a Página de Código 737 do Windows.</span><span class="sxs-lookup"><span data-stu-id="f3fc2-109">The following example shows how to convert a text file that has been encoded in 8-bit ASCII, interpreting the source text according to Windows Code Page 737.</span></span>  
  
 <span data-ttu-id="f3fc2-110">[!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="f3fc2-110">[!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3fc2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3fc2-111">See Also</span></span>  
 [<span data-ttu-id="f3fc2-112">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="f3fc2-112">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)

