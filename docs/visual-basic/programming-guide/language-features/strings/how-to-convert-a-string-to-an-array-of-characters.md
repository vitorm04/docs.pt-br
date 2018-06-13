---
title: Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648613"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="ecdd4-102">Como converter uma cadeia de caracteres em uma matriz de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecdd4-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="ecdd4-103">Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres, como quando você estiver analisando uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ecdd4-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="ecdd4-104">Este exemplo mostra como você pode obter uma matriz de caracteres em uma cadeia de caracteres chamando a cadeia de caracteres <xref:System.String.ToCharArray%2A> método.</span><span class="sxs-lookup"><span data-stu-id="ecdd4-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ecdd4-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecdd4-105">Example</span></span>  
 <span data-ttu-id="ecdd4-106">Este exemplo demonstra como dividir uma cadeia de caracteres em uma `Char` matriz e como dividir uma cadeia de caracteres em um `String` matriz de seus caracteres de texto Unicode.</span><span class="sxs-lookup"><span data-stu-id="ecdd4-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="ecdd4-107">A razão para essa distinção é que caracteres Unicode de texto podem ser compostos de dois ou mais `Char` caracteres (como um par substituto ou uma combinação sequência de caracteres).</span><span class="sxs-lookup"><span data-stu-id="ecdd4-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="ecdd4-108">Para obter mais informações, consulte <xref:System.Globalization.TextElementEnumerator> e "The Unicode Standard" em http://www.unicode.org.</span><span class="sxs-lookup"><span data-stu-id="ecdd4-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and "The Unicode Standard" at http://www.unicode.org.</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="ecdd4-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ecdd4-109">Example</span></span>  
 <span data-ttu-id="ecdd4-110">É mais difícil dividir uma cadeia de caracteres em seus caracteres Unicode de texto, mas isso é necessário se você precisar de informações sobre a representação visual de uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ecdd4-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="ecdd4-111">Este exemplo usa o <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> método para obter informações sobre os caracteres de texto Unicode que compõem uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ecdd4-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ecdd4-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ecdd4-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="ecdd4-113">Como acessar caracteres em cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="ecdd4-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="ecdd4-114">Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ecdd4-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="ecdd4-115">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="ecdd4-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
