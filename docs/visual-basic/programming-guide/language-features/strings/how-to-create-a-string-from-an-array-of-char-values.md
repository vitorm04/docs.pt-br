---
title: 'Como: criar uma cadeia de caracteres de uma matriz de valores de caracteres (Visual Basic) | Documentos do Microsoft'
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
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
caps.latest.revision: 10
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
ms.openlocfilehash: 12df19a88a3cc138b88bf012a70a35b5860ee5b8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a><span data-ttu-id="70238-102">Como criar uma cadeia de caracteres a partir de uma matriz de valores de caracteres (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70238-102">How to: Create a String from An Array of Char Values (Visual Basic)</span></span>
<span data-ttu-id="70238-103">Este exemplo cria a cadeia de caracteres "abcd" de caracteres individuais.</span><span class="sxs-lookup"><span data-stu-id="70238-103">This example creates the string "abcd" from individual characters.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70238-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="70238-104">Example</span></span>  
 <span data-ttu-id="70238-105">[!code-vb[VbVbalrStrings&#61;](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="70238-105">[!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="70238-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="70238-106">Compiling the Code</span></span>  
 <span data-ttu-id="70238-107">Este método não possui requisitos especiais.</span><span class="sxs-lookup"><span data-stu-id="70238-107">This method has no special requirements.</span></span>  
  
 <span data-ttu-id="70238-108">A sintaxe `"a"c`, onde um único `c` segue um único caractere entre aspas, é usada para criar um caractere literal.</span><span class="sxs-lookup"><span data-stu-id="70238-108">The syntax `"a"c`, where a single `c` follows a single character in quotation marks, is used to create a character literal.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="70238-109">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="70238-109">Robust Programming</span></span>  
 <span data-ttu-id="70238-110">Caracteres nulos (equivalente a `Chr(0)`) na sequência levar a resultados inesperados ao usar a cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="70238-110">Null characters (equivalent to `Chr(0)`) in the string lead to unexpected results when using the string.</span></span> <span data-ttu-id="70238-111">O caractere nulo será incluído com a cadeia de caracteres, mas caracteres após o caractere nulo não serão exibidos em algumas situações.</span><span class="sxs-lookup"><span data-stu-id="70238-111">The null character will be included with the string, but characters following the null character will not be displayed in some situations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70238-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70238-112">See Also</span></span>  
 <span data-ttu-id="70238-113"><xref:System.String></xref:System.String></span><span class="sxs-lookup"><span data-stu-id="70238-113"><xref:System.String></span></span>   
<span data-ttu-id="70238-114"> [Tipo de dados char](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="70238-114"> [Char Data Type](../../../../visual-basic/language-reference/data-types/char-data-type.md) </span></span>  
<span data-ttu-id="70238-115"> [Tipos de Dados](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span><span class="sxs-lookup"><span data-stu-id="70238-115"> [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md)</span></span>
