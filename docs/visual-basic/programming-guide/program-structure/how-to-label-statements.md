---
title: "Como rotular instruções (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 190ec9fc2392e6e4adae9b2b612edd69d73cedfd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="dfa1d-102">Como rotular instruções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfa1d-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="dfa1d-103">Blocos de instrução são compostos de linhas de código delimitado por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="dfa1d-104">Linhas de código precedido por uma cadeia de caracteres ou inteiro de identificação são consideradas *rotulada*.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="dfa1d-105">Rótulos de instruções são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="dfa1d-106">Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic, como aquelas que identificam os elementos de programação — ou literais inteiro.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="dfa1d-107">Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="dfa1d-108">O compilador identifica rótulos, verificando se o início da linha corresponde a qualquer identificador já definido.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="dfa1d-109">Se não existir, o compilador assumirá que seja um rótulo.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="dfa1d-110">Rótulos tem seu próprio espaço de declaração e não interferem em outros identificadores.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="dfa1d-111">Escopo do rótulo é o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="dfa1d-112">Declaração de rótulo terá precedência em qualquer situação ambígua.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dfa1d-113">Rótulos podem ser usados somente em declarações executáveis dentro dos métodos.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="dfa1d-114">Para identificar uma linha de código</span><span class="sxs-lookup"><span data-stu-id="dfa1d-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="dfa1d-115">Coloque um identificador, seguido por dois-pontos, no início da linha do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="dfa1d-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="dfa1d-116">Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="dfa1d-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     [!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dfa1d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfa1d-117">See Also</span></span>  
 [<span data-ttu-id="dfa1d-118">Instruções</span><span class="sxs-lookup"><span data-stu-id="dfa1d-118">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)  
 [<span data-ttu-id="dfa1d-119">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="dfa1d-119">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="dfa1d-120">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="dfa1d-120">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
