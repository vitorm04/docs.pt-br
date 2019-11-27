---
title: Como converter uma cadeia de caracteres em uma matriz de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352453"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="13e1b-102">Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13e1b-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="13e1b-103">Às vezes, é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres em sua cadeia de caracteres, como quando você está analisando uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="13e1b-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="13e1b-104">Este exemplo mostra como você pode obter uma matriz dos caracteres em uma cadeia de caracteres chamando o método de <xref:System.String.ToCharArray%2A> da cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="13e1b-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13e1b-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13e1b-105">Example</span></span>  
 <span data-ttu-id="13e1b-106">Este exemplo demonstra como dividir uma cadeia de caracteres em uma `Char` matriz e como dividir uma cadeia de caracteres em uma matriz `String` de seus caracteres de texto Unicode.</span><span class="sxs-lookup"><span data-stu-id="13e1b-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="13e1b-107">O motivo para essa distinção é que os caracteres de texto Unicode podem ser compostos de dois ou mais caracteres `Char` (como um par alternativo ou uma sequência de caracteres de combinação).</span><span class="sxs-lookup"><span data-stu-id="13e1b-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="13e1b-108">Para obter mais informações, consulte <xref:System.Globalization.TextElementEnumerator> e [o padrão Unicode](https://www.unicode.org/standard/standard.html).</span><span class="sxs-lookup"><span data-stu-id="13e1b-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="13e1b-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13e1b-109">Example</span></span>  
 <span data-ttu-id="13e1b-110">É mais difícil dividir uma String em seus caracteres de texto Unicode, mas isso é necessário se você precisar de informações sobre a representação visual de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="13e1b-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="13e1b-111">Este exemplo usa o método <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> para obter informações sobre os caracteres de texto Unicode que compõem uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="13e1b-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="13e1b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13e1b-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="13e1b-113">Como acessar caracteres em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="13e1b-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="13e1b-114">Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="13e1b-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="13e1b-115">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="13e1b-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
