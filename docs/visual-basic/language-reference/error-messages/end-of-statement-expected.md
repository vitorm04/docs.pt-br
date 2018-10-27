---
title: Fim de instrução esperado
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 8df756009ebe3a0613ec47018d938151829214df
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039017"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="700b6-102">Fim de instrução esperado</span><span class="sxs-lookup"><span data-stu-id="700b6-102">End of statement expected</span></span>
<span data-ttu-id="700b6-103">A instrução está sintaticamente completa, mas um elemento de programação adicional após o elemento que conclui a declaração.</span><span class="sxs-lookup"><span data-stu-id="700b6-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="700b6-104">Um terminador de linha é necessário no final de cada instrução.</span><span class="sxs-lookup"><span data-stu-id="700b6-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="700b6-105">Um terminador de linha divide os caracteres de um arquivo de origem do Visual Basic em linhas.</span><span class="sxs-lookup"><span data-stu-id="700b6-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="700b6-106">Exemplos de terminadores de linha são o Unicode carro retorno caractere (& HD), o Unicode avanço de linha caractere (& HA), e o Unicode retorno de carro seguido pelo caractere de avanço de linha Unicode do caractere.</span><span class="sxs-lookup"><span data-stu-id="700b6-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="700b6-107">Para obter mais informações sobre os terminadores de linha, consulte o [especificação da linguagem Visual Basic](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="700b6-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="700b6-108">**ID do erro:** BC30205</span><span class="sxs-lookup"><span data-stu-id="700b6-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="700b6-109">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="700b6-109">To correct this error</span></span>
  
1.  <span data-ttu-id="700b6-110">Verifique se as duas instruções diferentes inadvertidamente tem sido colocadas na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="700b6-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="700b6-111">Insira um terminador de linha após o elemento que conclui a declaração.</span><span class="sxs-lookup"><span data-stu-id="700b6-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="700b6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="700b6-112">See Also</span></span>  
 [<span data-ttu-id="700b6-113">Como quebrar e combinar instruções no código</span><span class="sxs-lookup"><span data-stu-id="700b6-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="700b6-114">Instruções</span><span class="sxs-lookup"><span data-stu-id="700b6-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
