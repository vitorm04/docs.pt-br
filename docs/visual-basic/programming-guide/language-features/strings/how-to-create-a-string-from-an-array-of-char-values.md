---
title: Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 08ad2f1c9455853e92533a7f00726c73b6adb87e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91071151"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="ab9c5-102">Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab9c5-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>

<span data-ttu-id="ab9c5-103">Este exemplo cria a cadeia "abcd" de caracteres individuais.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab9c5-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ab9c5-104">Example</span></span>  

 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="ab9c5-105">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="ab9c5-105">Compile the code</span></span>  

 <span data-ttu-id="ab9c5-106">Esse método não tem requisitos especiais.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-106">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="ab9c5-107">A sintaxe `"a"c` , em que um único `c` segue um único caractere entre aspas, é usada para criar um literal de caractere.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-107">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ab9c5-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="ab9c5-108">Robust Programming</span></span>  

 <span data-ttu-id="ab9c5-109">Caracteres nulos (equivalente a `Chr(0)` ) na cadeia de caracteres levam a resultados inesperados ao usar a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-109">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="ab9c5-110">O caractere nulo será incluído com a cadeia de caracteres, mas os caracteres após o caractere nulo não serão exibidos em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="ab9c5-110">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9c5-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="ab9c5-111">See also</span></span>

- <xref:System.String>
- [<span data-ttu-id="ab9c5-112">Tipo de Dados de Caractere</span><span class="sxs-lookup"><span data-stu-id="ab9c5-112">Char Data Type</span></span>](../../../language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="ab9c5-113">Data Types</span><span class="sxs-lookup"><span data-stu-id="ab9c5-113">Data Types</span></span>](../data-types/index.md)
