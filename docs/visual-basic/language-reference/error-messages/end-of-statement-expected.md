---
title: Fim de instrução esperado
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="de03f-102">Fim de instrução esperado</span><span class="sxs-lookup"><span data-stu-id="de03f-102">End of statement expected</span></span>
<span data-ttu-id="de03f-103">A instrução está sintaticamente completa, mas um elemento de programação adicional vem depois do elemento que conclui a declaração.</span><span class="sxs-lookup"><span data-stu-id="de03f-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="de03f-104">Um terminador de linha é necessário no final de cada instrução.</span><span class="sxs-lookup"><span data-stu-id="de03f-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="de03f-105">Um terminador de linha divide os caracteres de um arquivo de origem do Visual Basic em linhas.</span><span class="sxs-lookup"><span data-stu-id="de03f-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="de03f-106">Exemplos de terminadores de linha são o Unicode carro retorno caractere (& HD), o Unicode avanço de linha caractere (& HA), e o Unicode retorno de carro seguido pelo caractere de avanço de linha Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="de03f-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="de03f-107">Para obter mais informações sobre os terminadores de linha, consulte o [especificação da linguagem Visual Basic](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="de03f-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="de03f-108">**ID do erro:** BC30205</span><span class="sxs-lookup"><span data-stu-id="de03f-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="de03f-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="de03f-109">To correct this error</span></span>
  
1.  <span data-ttu-id="de03f-110">Verifique se duas declarações diferentes foram inadvertidamente colocadas na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="de03f-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="de03f-111">Insira um terminador de linha após o elemento que conclui a declaração.</span><span class="sxs-lookup"><span data-stu-id="de03f-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="de03f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="de03f-112">See Also</span></span>  
 [<span data-ttu-id="de03f-113">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="de03f-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="de03f-114">Instruções</span><span class="sxs-lookup"><span data-stu-id="de03f-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
