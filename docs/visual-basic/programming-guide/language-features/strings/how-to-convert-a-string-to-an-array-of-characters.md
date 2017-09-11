---
title: 'Como: converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- character arrays, converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 47b35f8324037ca8c2235e8ae5ab644bfde3a027
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="74653-102">Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="74653-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="74653-103">Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres, como quando você estiver analisando uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="74653-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="74653-104">Este exemplo mostra como você pode obter uma matriz de caracteres em uma cadeia de caracteres chamando a cadeia de caracteres <xref:System.String.ToCharArray%2A>método.</xref:System.String.ToCharArray%2A></span><span class="sxs-lookup"><span data-stu-id="74653-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="74653-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74653-105">Example</span></span>  
 <span data-ttu-id="74653-106">Este exemplo demonstra como dividir uma cadeia de caracteres em uma `Char` matriz e como dividir uma cadeia de caracteres em um `String` matriz de seus caracteres de texto Unicode.</span><span class="sxs-lookup"><span data-stu-id="74653-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="74653-107">A razão para essa distinção é que caracteres Unicode de texto podem ser compostos de dois ou mais `Char` caracteres (como um par substituto ou uma combinação sequência de caracteres).</span><span class="sxs-lookup"><span data-stu-id="74653-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="74653-108">Para obter mais informações, consulte <xref:System.Globalization.TextElementEnumerator>e "The Unicode Standard" em http://www.unicode.org.</xref:System.Globalization.TextElementEnumerator></span><span class="sxs-lookup"><span data-stu-id="74653-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 <span data-ttu-id="74653-109">[!code-vb[VbVbalrStrings&#75;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="74653-109">[!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="74653-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="74653-110">Example</span></span>  
 <span data-ttu-id="74653-111">É mais difícil dividir uma cadeia de caracteres em seus caracteres Unicode de texto, mas isso é necessário se você precisar de informações sobre a representação visual de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="74653-111">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="74653-112">Este exemplo usa o <xref:System.Globalization.StringInfo.SubstringByTextElements%2A>método para obter informações sobre os caracteres de texto Unicode que compõem uma cadeia de caracteres.</xref:System.Globalization.StringInfo.SubstringByTextElements%2A></span><span class="sxs-lookup"><span data-stu-id="74653-112">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 <span data-ttu-id="74653-113">[!code-vb[VbVbalrStrings&#76;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="74653-113">[!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74653-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74653-114">See Also</span></span>  
 <span data-ttu-id="74653-115"><xref:System.String.Chars%2A></xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="74653-115"><xref:System.String.Chars%2A></span></span>   
 <span data-ttu-id="74653-116"><xref:System.Globalization.StringInfo?displayProperty=fullName></xref:System.Globalization.StringInfo?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="74653-116"><xref:System.Globalization.StringInfo?displayProperty=fullName></span></span>   
<span data-ttu-id="74653-117"> [Como: acessar caracteres em cadeias de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md) </span><span class="sxs-lookup"><span data-stu-id="74653-117"> [How to: Access Characters in Strings](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md) </span></span>  
<span data-ttu-id="74653-118"> [Convertendo entre cadeias de caracteres e outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="74653-118"> [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md) </span></span>  
<span data-ttu-id="74653-119"> [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)</span><span class="sxs-lookup"><span data-stu-id="74653-119"> [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)</span></span>
