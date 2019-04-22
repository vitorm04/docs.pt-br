---
title: 'Como: Caracteres de acesso em cadeias de caracteres no Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 840a769b0bb322ef7b878a312437c5ec200ab074
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834485"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="50aab-102">Como: Caracteres de acesso em cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50aab-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="50aab-103">Este exemplo demonstra como usar o <xref:System.String.Chars%2A> propriedade para acessar o caractere no local especificado em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="50aab-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50aab-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50aab-104">Example</span></span>  
 <span data-ttu-id="50aab-105">Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="50aab-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="50aab-106">Você pode pensar em uma cadeia de caracteres como uma matriz de caracteres (`Char` instâncias); você pode recuperar um determinado caractere consultando o índice do caractere através de <xref:System.String.Chars%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="50aab-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="50aab-107">O `index` parâmetro do <xref:System.String.Chars%2A> propriedade é baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="50aab-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="50aab-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="50aab-108">Robust Programming</span></span>  
 <span data-ttu-id="50aab-109">O <xref:System.String.Chars%2A> propriedade retorna o caractere na posição especificada.</span><span class="sxs-lookup"><span data-stu-id="50aab-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="50aab-110">No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere.</span><span class="sxs-lookup"><span data-stu-id="50aab-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="50aab-111">Para obter mais informações sobre como trabalhar com caracteres Unicode, consulte [como: Converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="50aab-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="50aab-112">O <xref:System.String.Chars%2A> propriedade gera uma <xref:System.IndexOutOfRangeException> exceção se o `index` parâmetro é maior que ou igual ao comprimento da cadeia de caracteres, ou se ele for menor que zero</span><span class="sxs-lookup"><span data-stu-id="50aab-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50aab-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50aab-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="50aab-114">Como: Converter uma cadeia de caracteres em uma matriz de caracteres</span><span class="sxs-lookup"><span data-stu-id="50aab-114">How to: Convert a String to an Array of Characters</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="50aab-115">Convertendo cadeias de caracteres em outros tipos de dados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="50aab-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="50aab-116">Cadeias de Caracteres</span><span class="sxs-lookup"><span data-stu-id="50aab-116">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
