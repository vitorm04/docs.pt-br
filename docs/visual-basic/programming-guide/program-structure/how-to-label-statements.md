---
title: "Como: rotular instruções (Visual Basic) | Documentos do Microsoft"
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
- colons (:)
- statements [Visual Basic], labels
- ': separator character'
- Visual Basic code, labeling statements
ms.assetid: 38f1ff43-2054-42cb-963b-1998e60c6ed4
caps.latest.revision: 18
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
ms.openlocfilehash: d7aad1a0d1b893b34348008dc436b29b4afd9627
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-label-statements-visual-basic"></a><span data-ttu-id="70247-102">Como rotular instruções (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="70247-102">How to: Label Statements (Visual Basic)</span></span>
<span data-ttu-id="70247-103">Blocos de instrução são compostos de linhas de código delimitado por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="70247-103">Statement blocks are made up of lines of code delimited by colons.</span></span> <span data-ttu-id="70247-104">Linhas de código precedida por uma cadeia de caracteres ou inteiro de identificação são consideradas *rotulado*.</span><span class="sxs-lookup"><span data-stu-id="70247-104">Lines of code preceded by an identifying string or integer are said to be *labeled*.</span></span> <span data-ttu-id="70247-105">Rótulos de instruções são usados para marcar uma linha de código para identificá-lo para uso com instruções de como `On Error Goto`.</span><span class="sxs-lookup"><span data-stu-id="70247-105">Statement labels are used to mark a line of code to identify it for use with statements such as `On Error Goto`.</span></span>  
  
 <span data-ttu-id="70247-106">Rótulos podem ser qualquer um dos identificadores válidos do Visual Basic, como aquelas que identificam os elementos de programação — ou literais inteiro.</span><span class="sxs-lookup"><span data-stu-id="70247-106">Labels may be either valid Visual Basic identifiers—such as those that identify programming elements—or integer literals.</span></span> <span data-ttu-id="70247-107">Um rótulo deve aparecer no início de uma linha de código-fonte e deve ser seguido por dois-pontos, independentemente se ele é seguido por uma instrução na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="70247-107">A label must appear at the beginning of a line of source code and must be followed by a colon, regardless of whether it is followed by a statement on the same line.</span></span>  
  
 <span data-ttu-id="70247-108">O compilador identifica rótulos, verificando se o início da linha coincide com nenhum identificador já definido.</span><span class="sxs-lookup"><span data-stu-id="70247-108">The compiler identifies labels by checking whether the beginning of the line matches any already-defined identifier.</span></span> <span data-ttu-id="70247-109">Se não existir, o compilador pressupõe que ele é um rótulo.</span><span class="sxs-lookup"><span data-stu-id="70247-109">If it does not, the compiler assumes it is a label.</span></span>  
  
 <span data-ttu-id="70247-110">Rótulos tem seu próprio espaço de declaração e não interferem em outros identificadores.</span><span class="sxs-lookup"><span data-stu-id="70247-110">Labels have their own declaration space and do not interfere with other identifiers.</span></span> <span data-ttu-id="70247-111">Escopo do rótulo é o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="70247-111">A label's scope is the body of the method.</span></span> <span data-ttu-id="70247-112">Declaração de rótulo terá precedência em qualquer situação ambígua.</span><span class="sxs-lookup"><span data-stu-id="70247-112">Label declaration takes precedence in any ambiguous situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70247-113">Rótulos podem ser usados somente em declarações executáveis dentro métodos.</span><span class="sxs-lookup"><span data-stu-id="70247-113">Labels can be used only on executable statements inside methods.</span></span>  
  
### <a name="to-label-a-line-of-code"></a><span data-ttu-id="70247-114">Para rotular uma linha de código</span><span class="sxs-lookup"><span data-stu-id="70247-114">To label a line of code</span></span>  
  
-   <span data-ttu-id="70247-115">Coloque um identificador, seguido por dois-pontos, no início da linha de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="70247-115">Place an identifier, followed by a colon, at the beginning of the line of source code.</span></span>  
  
     <span data-ttu-id="70247-116">Por exemplo, as seguintes linhas de código são rotuladas com `Jump` e `120`, respectivamente:</span><span class="sxs-lookup"><span data-stu-id="70247-116">For example, the following lines of code are labeled with `Jump` and `120`, respectively:</span></span>  
  
     <span data-ttu-id="70247-117">[!code-vb[VbVbalrStatements&#708;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="70247-117">[!code-vb[VbVbalrStatements#708](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/how-to-label-statements_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70247-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70247-118">See Also</span></span>  
 <span data-ttu-id="70247-119">[Instruções](../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="70247-119">[Statements](../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="70247-120"> [Nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="70247-120"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="70247-121"> [Estrutura do Programa e Convenções de Código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)</span><span class="sxs-lookup"><span data-stu-id="70247-121"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)</span></span>
