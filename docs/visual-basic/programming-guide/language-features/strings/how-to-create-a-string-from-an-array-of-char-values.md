---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344395"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="a0a99-102">Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0a99-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="a0a99-103">Este exemplo cria a cadeia "abcd" de caracteres individuais.</span><span class="sxs-lookup"><span data-stu-id="a0a99-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0a99-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a0a99-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a0a99-105">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="a0a99-105">Compiling the Code</span></span>  
 <span data-ttu-id="a0a99-106">Esse método não tem requisitos especiais.</span><span class="sxs-lookup"><span data-stu-id="a0a99-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="a0a99-107">A sintaxe `"a"c`, em que uma única `c` segue um único caractere entre aspas, é usada para criar um literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="a0a99-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a0a99-108">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="a0a99-108">Robust Programming</span></span>  
 <span data-ttu-id="a0a99-109">Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levam a resultados inesperados ao usar a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a0a99-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="a0a99-110">O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="a0a99-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a99-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0a99-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="a0a99-112">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="a0a99-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="a0a99-113">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="a0a99-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
