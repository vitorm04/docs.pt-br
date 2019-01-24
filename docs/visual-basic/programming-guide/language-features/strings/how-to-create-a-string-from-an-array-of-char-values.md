---
title: 'Como: Criar uma cadeia de caracteres de uma matriz de valores Char (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: a067474d6b32589a34b031d5c3ea4e5a4be55834
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611456"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="45732-102">Como: Criar uma cadeia de caracteres de uma matriz de valores Char (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45732-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="45732-103">Este exemplo cria a cadeia de caracteres "abcd" dos caracteres individuais.</span><span class="sxs-lookup"><span data-stu-id="45732-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45732-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45732-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45732-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="45732-105">Compiling the Code</span></span>  
 <span data-ttu-id="45732-106">Esse método não tem nenhum requisito especial.</span><span class="sxs-lookup"><span data-stu-id="45732-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="45732-107">A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usado para criar um caractere literal.</span><span class="sxs-lookup"><span data-stu-id="45732-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="45732-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="45732-108">Robust Programming</span></span>  
 <span data-ttu-id="45732-109">Caracteres nulos (equivalente a `Chr(0)`) na cadeia de caracteres levar a resultados inesperados ao usar a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="45732-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="45732-110">O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="45732-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45732-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45732-111">See also</span></span>
- <xref:System.String>
- [<span data-ttu-id="45732-112">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="45732-112">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="45732-113">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="45732-113">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
