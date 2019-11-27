---
title: Como quebrar e combinar instruções no código
ms.date: 07/20/2015
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
ms.openlocfilehash: f1a24c001cd20acc7663fb4cbe60e7e35a9c8fc3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347436"
---
# <a name="how-to-break-and-combine-statements-in-code-visual-basic"></a><span data-ttu-id="3f200-102">Como quebrar e combinar instruções no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3f200-102">How to: Break and Combine Statements in Code (Visual Basic)</span></span>

<span data-ttu-id="3f200-103">Ao escrever seu código, você pode ocasionalmente criar instruções demoradas que exigem a rolagem horizontal no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="3f200-103">When writing your code, you might at times create lengthy statements that necessitate horizontal scrolling in the Code Editor.</span></span> <span data-ttu-id="3f200-104">Embora isso não afete a maneira como seu código é executado, ele dificulta a leitura do código conforme ele aparece no monitor.</span><span class="sxs-lookup"><span data-stu-id="3f200-104">Although this doesn't affect the way your code runs, it makes it difficult for you or anyone else to read the code as it appears on the monitor.</span></span> <span data-ttu-id="3f200-105">Nesses casos, você deve considerar dividir a única instrução longa em várias linhas.</span><span class="sxs-lookup"><span data-stu-id="3f200-105">In such cases, you should consider breaking the single long statement into several lines.</span></span>

## <a name="to-break-a-single-statement-into-multiple-lines"></a><span data-ttu-id="3f200-106">Para dividir uma única instrução em várias linhas</span><span class="sxs-lookup"><span data-stu-id="3f200-106">To break a single statement into multiple lines</span></span>

<span data-ttu-id="3f200-107">Use o caractere de continuação de linha, que é um sublinhado (`_`), no ponto em que você deseja que a linha seja quebrada.</span><span class="sxs-lookup"><span data-stu-id="3f200-107">Use the line-continuation character, which is an underscore (`_`), at the point at which you want the line to break.</span></span> <span data-ttu-id="3f200-108">O sublinhado deve ser imediatamente precedido por um espaço e imediatamente seguido por um terminador de linha (retorno de carro) ou (começando com a versão 16,0) um comentário seguido por um retorno de carro.</span><span class="sxs-lookup"><span data-stu-id="3f200-108">The underscore must be immediately preceded by a space and immediately followed by a line terminator (carriage return) or (starting with version 16.0) a comment followed by a carriage return.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3f200-109">Em alguns casos, se você omitir o caractere de continuação de linha, o compilador de Visual Basic irá continuar implicitamente a instrução na próxima linha de código.</span><span class="sxs-lookup"><span data-stu-id="3f200-109">In some cases, if you omit the line-continuation character, the Visual Basic compiler will implicitly continue the statement on the next line of code.</span></span> <span data-ttu-id="3f200-110">Para obter uma lista de elementos de sintaxe para os quais você pode omitir o caractere de continuação de linha, consulte "continuação de linha implícita" em [instruções](../../../visual-basic/programming-guide/language-features/statements.md).</span><span class="sxs-lookup"><span data-stu-id="3f200-110">For a list of syntax elements for which you can omit the line-continuation character, see "Implicit Line Continuation" in [Statements](../../../visual-basic/programming-guide/language-features/statements.md).</span></span>

  <span data-ttu-id="3f200-111">No exemplo a seguir, a instrução é dividida em quatro linhas com caracteres de continuação de linha encerrando tudo menos a última linha.</span><span class="sxs-lookup"><span data-stu-id="3f200-111">In the following example, the statement is broken into four lines with line-continuation characters terminating all but the last line.</span></span>

  [!code-vb[VbVbcnConventions#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#20)]

  <span data-ttu-id="3f200-112">Usar essa sequência torna seu código mais fácil de ler, tanto online quanto quando impresso.</span><span class="sxs-lookup"><span data-stu-id="3f200-112">Using this sequence makes your code easier to read, both online and when printed.</span></span>

  <span data-ttu-id="3f200-113">O caractere de continuação de linha deve ser o último caractere em uma linha.</span><span class="sxs-lookup"><span data-stu-id="3f200-113">The line-continuation character must be the last character on a line.</span></span> <span data-ttu-id="3f200-114">Você não pode acompanhá-lo com nada mais na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="3f200-114">You can't follow it with anything else on the same line.</span></span>

  <span data-ttu-id="3f200-115">Existem algumas limitações para onde você pode usar o caractere de continuação de linha; por exemplo, você não pode usá-lo no meio de um nome de argumento.</span><span class="sxs-lookup"><span data-stu-id="3f200-115">Some limitations exist as to where you can use the line-continuation character; for example, you can't use it in the middle of an argument name.</span></span> <span data-ttu-id="3f200-116">Você pode quebrar uma lista de argumentos com o caractere de continuação de linha, mas os nomes individuais dos argumentos devem permanecer intactos.</span><span class="sxs-lookup"><span data-stu-id="3f200-116">You can break an argument list with the line-continuation character, but the individual names of the arguments must remain intact.</span></span>

  <span data-ttu-id="3f200-117">Você não pode continuar um comentário usando um caractere de continuação de linha.</span><span class="sxs-lookup"><span data-stu-id="3f200-117">You can't continue a comment by using a line-continuation character.</span></span> <span data-ttu-id="3f200-118">O compilador não examina os caracteres em um comentário para obter um significado especial.</span><span class="sxs-lookup"><span data-stu-id="3f200-118">The compiler doesn't examine the characters in a comment for special meaning.</span></span> <span data-ttu-id="3f200-119">Para um comentário de várias linhas, repita o símbolo de comentário (`'`) em cada linha.</span><span class="sxs-lookup"><span data-stu-id="3f200-119">For a multiple-line comment, repeat the comment symbol (`'`) on each line.</span></span>

 <span data-ttu-id="3f200-120">Embora colocar cada instrução em uma linha separada seja o método recomendado, Visual Basic também permite colocar várias instruções na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="3f200-120">Although placing each statement on a separate line is the recommended method, Visual Basic also allows you to place multiple statements on the same line.</span></span>

## <a name="to-place-multiple-statements-on-the-same-line"></a><span data-ttu-id="3f200-121">Para posicionar várias instruções na mesma linha</span><span class="sxs-lookup"><span data-stu-id="3f200-121">To place multiple statements on the same line</span></span>

<span data-ttu-id="3f200-122">Separe as instruções com dois-pontos (`:`), como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="3f200-122">Separate the statements with a colon (`:`), as in the following example:</span></span>

  [!code-vb[VbVbcnConventions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#10)]

## <a name="see-also"></a><span data-ttu-id="3f200-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f200-123">See also</span></span>

- [<span data-ttu-id="3f200-124">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="3f200-124">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="3f200-125">Instruções</span><span class="sxs-lookup"><span data-stu-id="3f200-125">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
