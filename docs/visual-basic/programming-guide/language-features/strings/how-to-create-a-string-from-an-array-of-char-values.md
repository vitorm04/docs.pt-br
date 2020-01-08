---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: bf37ceba901e712df10ad4b39f9ad74194843136
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346766"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="64041-102">Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64041-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="64041-103">Este exemplo cria a cadeia "abcd" de caracteres individuais.</span><span class="sxs-lookup"><span data-stu-id="64041-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64041-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64041-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="64041-105">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="64041-105">Compile the code</span></span>  
 <span data-ttu-id="64041-106">Esse método não tem requisitos especiais.</span><span class="sxs-lookup"><span data-stu-id="64041-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="64041-107">A sintaxe `"a"c`, em que uma única `c` segue um único caractere entre aspas, é usada para criar um literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="64041-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="64041-108">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="64041-108">Robust Programming</span></span>  
 <span data-ttu-id="64041-109">Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levam a resultados inesperados ao usar a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="64041-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="64041-110">O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="64041-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64041-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="64041-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="64041-112">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="64041-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="64041-113">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="64041-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
