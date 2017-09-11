---
title: 'Como: acessar caracteres em cadeias de caracteres no Visual Basic | Documentos do Microsoft'
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
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: 8
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
ms.openlocfilehash: 3c38dc1187210f7ab7376caf4c43e9fa73e35006
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a><span data-ttu-id="62f69-102">Como acessar caracteres em cadeias de caracteres no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62f69-102">How to: Access Characters in Strings in Visual Basic</span></span>
<span data-ttu-id="62f69-103">Este exemplo demonstra como usar o <xref:System.String.Chars%2A>propriedade para acessar o caractere no local especificado em uma cadeia de caracteres.</xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="62f69-103">This example demonstrates how to use the <xref:System.String.Chars%2A> property to access the character at the specified location in a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62f69-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="62f69-104">Example</span></span>  
 <span data-ttu-id="62f69-105">Às vezes é útil ter dados sobre os caracteres na cadeia de caracteres e as posições desses caracteres na cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="62f69-105">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string.</span></span> <span data-ttu-id="62f69-106">Você pode pensar em uma cadeia de caracteres como uma matriz de caracteres (`Char` instâncias); você pode recuperar um determinado caractere consultando o índice do caractere através do <xref:System.String.Chars%2A>propriedade.</xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="62f69-106">You can think of a string as an array of characters (`Char` instances); you can retrieve a particular character by referencing the index of that character through the <xref:System.String.Chars%2A> property.</span></span>  
  
 <span data-ttu-id="62f69-107">[!code-vb[49 VbVbalrStrings](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="62f69-107">[!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]</span></span>  
  
 <span data-ttu-id="62f69-108">O `index` parâmetro o <xref:System.String.Chars%2A>propriedade é baseada em zero.</xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="62f69-108">The `index` parameter of the <xref:System.String.Chars%2A> property is zero-based.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="62f69-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="62f69-109">Robust Programming</span></span>  
 <span data-ttu-id="62f69-110">O <xref:System.String.Chars%2A>propriedade retorna o caractere na posição especificada.</xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="62f69-110">The <xref:System.String.Chars%2A> property returns the character at the specified position.</span></span> <span data-ttu-id="62f69-111">No entanto, alguns caracteres Unicode podem ser representados por mais de um caractere.</span><span class="sxs-lookup"><span data-stu-id="62f69-111">However, some Unicode characters can be represented by more than one character.</span></span> <span data-ttu-id="62f69-112">Para obter mais informações sobre como trabalhar com caracteres Unicode, consulte [como: converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span><span class="sxs-lookup"><span data-stu-id="62f69-112">For more information on how to work with Unicode characters, see [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).</span></span>  
  
 <span data-ttu-id="62f69-113">O <xref:System.String.Chars%2A>propriedade lança um <xref:System.IndexOutOfRangeException>exceção se o `index` parâmetro for maior ou igual ao comprimento da cadeia de caracteres, ou se ele for menor que zero</xref:System.IndexOutOfRangeException> </xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="62f69-113">The <xref:System.String.Chars%2A> property throws an <xref:System.IndexOutOfRangeException> exception if the `index` parameter is greater than or equal to the length of the string, or if it is less than zero</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62f69-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="62f69-114">See Also</span></span>  
 <span data-ttu-id="62f69-115"><xref:System.String.Chars%2A></xref:System.String.Chars%2A></span><span class="sxs-lookup"><span data-stu-id="62f69-115"><xref:System.String.Chars%2A></span></span>   
<span data-ttu-id="62f69-116"> [Como: converter uma cadeia de caracteres em uma matriz de caracteres](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md) </span><span class="sxs-lookup"><span data-stu-id="62f69-116"> [How to: Convert a String to an Array of Characters](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md) </span></span>  
<span data-ttu-id="62f69-117"> [Convertendo entre cadeias de caracteres e outros tipos de dados no Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="62f69-117"> [Converting Between Strings and Other Data Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md) </span></span>  
<span data-ttu-id="62f69-118"> [Cadeias de Caracteres](../../../../visual-basic/programming-guide/language-features/strings/index.md)</span><span class="sxs-lookup"><span data-stu-id="62f69-118"> [Strings](../../../../visual-basic/programming-guide/language-features/strings/index.md)</span></span>
