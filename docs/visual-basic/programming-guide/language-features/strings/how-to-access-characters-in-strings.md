---
title: Como acessar caracteres em cadeias de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 4ea37c4393a8ece5513327b22c6c0ba4b027c781
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059178"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="85eca-102">Como acessar caracteres em cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85eca-102">How to: Access Characters in Strings in Visual Basic</span></span>

<span data-ttu-id="85eca-103">Este exemplo demonstra como usar a <xref:System.String.Chars%2A> propriedade para acessar o caractere no local especificado em uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85eca-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85eca-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85eca-104">Example</span></span>  

 <span data-ttu-id="85eca-105">Às vezes, é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="85eca-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="85eca-106">Você pode considerar uma cadeia de caracteres como uma matriz de personagens ( `Char` instâncias); você pode recuperar um caractere específico referenciando o índice desse caractere por meio da <xref:System.String.Chars%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="85eca-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <span data-ttu-id="85eca-107">O `index` parâmetro da <xref:System.String.Chars%2A> propriedade é baseado em zero.</span><span class="sxs-lookup"><span data-stu-id="85eca-107">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="85eca-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="85eca-108">Robust Programming</span></span>  

 <span data-ttu-id="85eca-109">A <xref:System.String.Chars%2A> propriedade retorna o caractere na posição especificada.</span><span class="sxs-lookup"><span data-stu-id="85eca-109">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="85eca-110">No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere.</span><span class="sxs-lookup"><span data-stu-id="85eca-110">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="85eca-111">Para saber mais sobre como trabalhar com caracteres Unicode, confira [como converter uma cadeia de caracteres em uma matriz de caracteres](how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="85eca-111">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="85eca-112">A <xref:System.String.Chars%2A> propriedade gera uma <xref:System.IndexOutOfRangeException> exceção se o `index` parâmetro for maior ou igual ao comprimento da cadeia de caracteres, ou se for menor que zero</span><span class="sxs-lookup"><span data-stu-id="85eca-112">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85eca-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="85eca-113">See also</span></span>

- <xref:System.String.Chars%2A>
- [<span data-ttu-id="85eca-114">Como converter uma cadeia de caracteres em uma matriz de caracteres</span><span class="sxs-lookup"><span data-stu-id="85eca-114">How to: Convert a String to an Array of Characters</span></span>](how-to-convert-a-string-to-an-array-of-characters.md)
- [<span data-ttu-id="85eca-115">Convertendo entre cadeias de caracteres e outros tipos de dados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="85eca-115">Converting Between Strings and Other Data Types in Visual Basic</span></span>](converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="85eca-116">Cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="85eca-116">Strings</span></span>](index.md)
