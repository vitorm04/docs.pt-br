---
title: Como quebrar e combinar instruções no código (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb._
helpviewer_keywords:
- colons (:)
- line continuation
- _ line-continuation character
- ': line separator character'
- Visual Basic code, line breaks in
- Visual Basic code, line breaks
- Visual Basic code, line continuation
- long lines of code
- line terminator
- line-continuation sequence
- underscores [Visual Basic], in code
- statements [Visual Basic], line continuation in
- line breaks [Visual Basic], in code
- line-continuation character [Visual Basic]
- Visual Basic code, line continuation in
- statements [Visual Basic], line breaks in
ms.assetid: dea01dad-a8ac-484a-bb3a-8c45a1b1eccc
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf6b3ce7e5f9549ca04c4980bd3c91513b343ff6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="07c9e-102">Como quebrar e combinar instruções no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07c9e-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>
<span data-ttu-id="07c9e-103">Ao escrever seu código, às vezes você pode criar instruções longas que necessitam de rolagem horizontal no Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="07c9e-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="07c9e-104">Embora isso não afeta a maneira como o código é executado, ele torna difícil para você ou outra pessoa para ler o código como ele aparece no monitor.</span><span class="sxs-lookup"><span data-stu-id="07c9e-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="07c9e-105">Nesses casos, você deve considerar a única instrução longo de quebra em várias linhas.</span><span class="sxs-lookup"><span data-stu-id="07c9e-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>  
  
### <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="07c9e-106">Para dividir uma única instrução em várias linhas</span><span class="sxs-lookup"><span data-stu-id="07c9e-106">To break a single statement into multiple lines</span></span>  
  
-   <span data-ttu-id="07c9e-107">Use o caractere de continuação de linha, que é um caractere de sublinhado (`_`), o ponto no qual você deseja que a linha de quebra.</span><span class="sxs-lookup"><span data-stu-id="07c9e-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="07c9e-108">O sublinhado deve ser imediatamente precedido por um espaço e seguido imediatamente por um terminador de linha (retorno de carro).</span><span class="sxs-lookup"><span data-stu-id="07c9e-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07c9e-109">Em alguns casos, se você omitir o caractere de continuação de linha, o compilador do Visual Basic continuará implicitamente a instrução na próxima linha de código.</span><span class="sxs-lookup"><span data-stu-id="07c9e-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="07c9e-110">Para obter uma lista de elementos de sintaxe para a qual você pode omitir o caractere de continuação de linha, consulte "Continuação de linha implícita" [instruções](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="07c9e-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>  
  
     <span data-ttu-id="07c9e-111">No exemplo a seguir, a instrução é dividida em quatro linhas com caracteres de continuação de linha, encerrando todas, mas a última linha.</span><span class="sxs-lookup"><span data-stu-id="07c9e-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>  
  
     [!code-vb[VbVbcnConventions#20](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_1.vb)]  
  
     <span data-ttu-id="07c9e-112">Usar esta sequência torna o código mais fácil de ler, online e quando impresso.</span><span class="sxs-lookup"><span data-stu-id="07c9e-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>  
  
     <span data-ttu-id="07c9e-113">O caractere de continuação de linha deve ser o último caractere em uma linha.</span><span class="sxs-lookup"><span data-stu-id="07c9e-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="07c9e-114">Você não pode segui-lo com qualquer outra coisa na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="07c9e-114">You can't follow it with anything else on the same line.</span></span>  
  
     <span data-ttu-id="07c9e-115">Existem algumas limitações sobre onde você pode usar o caractere de continuação de linha; Por exemplo, você não pode usá-lo no meio de um nome de argumento.</span><span class="sxs-lookup"><span data-stu-id="07c9e-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="07c9e-116">Você pode dividir a lista de argumentos com o caractere de continuação de linha, mas os nomes individuais dos argumentos devem permanecer intactos.</span><span class="sxs-lookup"><span data-stu-id="07c9e-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>  
  
     <span data-ttu-id="07c9e-117">Você não pode continuar um comentário usando um caractere de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="07c9e-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="07c9e-118">O compilador não examina os caracteres em um comentário para um significado especial.</span><span class="sxs-lookup"><span data-stu-id="07c9e-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="07c9e-119">Para um comentário de várias linhas, repita o símbolo de comentário (`'`) em cada linha.</span><span class="sxs-lookup"><span data-stu-id="07c9e-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>  
  
 <span data-ttu-id="07c9e-120">Embora a colocação de cada instrução em uma linha separada é o método recomendado, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] também permite que você coloque várias instruções na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="07c9e-120">Although placing each statement on a separate line is the recommended method, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] also allows you to place multiple statements on the same line.</span></span>  
  
### <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="07c9e-121">Para colocar várias instruções na mesma linha</span><span class="sxs-lookup"><span data-stu-id="07c9e-121">To place multiple statements on the same line</span></span>  
  
-   <span data-ttu-id="07c9e-122">Separe as instruções com dois-pontos (`:`), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="07c9e-122">Separate the statements with a colon (`:`), as in the following example.</span></span>  
  
     [!code-vb[VbVbcnConventions#10](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/how-to-break-and-combine-statements-in-code_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="07c9e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07c9e-123">See Also</span></span>  
 [<span data-ttu-id="07c9e-124">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="07c9e-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="07c9e-125">Instruções</span><span class="sxs-lookup"><span data-stu-id="07c9e-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
