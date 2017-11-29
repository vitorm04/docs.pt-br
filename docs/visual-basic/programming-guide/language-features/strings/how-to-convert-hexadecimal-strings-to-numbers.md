---
title: "Como converter cadeias de caracteres hexadecimais em números (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6b1beae273fa737ca7c95a253d95c947e760f9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="97c68-102">Como converter cadeias de caracteres hexadecimais em números (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="97c68-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="97c68-103">Este exemplo converte uma cadeia de caracteres hexadecimal em um número inteiro usando o <xref:System.Convert.ToInt32%2A> método.</span><span class="sxs-lookup"><span data-stu-id="97c68-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A> method.</span></span>  
  
### <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="97c68-104">Para converter uma cadeia de caracteres hexadecimal em um número</span><span class="sxs-lookup"><span data-stu-id="97c68-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="97c68-105">Use o <xref:System.Convert.ToInt32%2A> método para converter o número expressado na base-16 como um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="97c68-105">Use the <xref:System.Convert.ToInt32%2A> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="97c68-106">O primeiro argumento do <xref:System.Convert.ToInt32%2A> método é a cadeia de caracteres para converter.</span><span class="sxs-lookup"><span data-stu-id="97c68-106">The first argument of the <xref:System.Convert.ToInt32%2A> method is the string to convert.</span></span> <span data-ttu-id="97c68-107">O segundo argumento descreve qual base o número é expresso; hexadecimal é base 16.</span><span class="sxs-lookup"><span data-stu-id="97c68-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[VbVbalrStrings#62](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="97c68-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97c68-108">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A>
