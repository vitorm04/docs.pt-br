---
title: Comentários no código (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
ms.openlocfilehash: 4486b5be42f4a356b2017fe8629bc96f6ad47eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650963"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="f56a0-102">Comentários no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f56a0-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="f56a0-103">À medida que você lê os exemplos de código, você encontra geralmente o símbolo de comentário (`'`).</span><span class="sxs-lookup"><span data-stu-id="f56a0-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="f56a0-104">Este símbolo informa ao compilador do Visual Basic para ignorar o texto a seguir, ou o *comentário*.</span><span class="sxs-lookup"><span data-stu-id="f56a0-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="f56a0-105">Os comentários são uma breve explicação e/ou anotações adicionadas ao código para o benefício de quem os lê.</span><span class="sxs-lookup"><span data-stu-id="f56a0-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="f56a0-106">É uma prática de programação recomendável iniciar todos os procedimentos com um breve comentário descrevendo as características do procedimento e sua funcionalidade (o que ele faz).</span><span class="sxs-lookup"><span data-stu-id="f56a0-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="f56a0-107">Isso é um benefício para o programador e é vantajoso para qualquer pessoa que examinar o código.</span><span class="sxs-lookup"><span data-stu-id="f56a0-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="f56a0-108">Você deve separar os detalhes de implementação (como o procedimento faz isso) dos comentários que descrevem as características funcionais.</span><span class="sxs-lookup"><span data-stu-id="f56a0-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="f56a0-109">Quando você incluir detalhes da implementação na descrição, lembre-se de atualizá-los quando você atualizar a função.</span><span class="sxs-lookup"><span data-stu-id="f56a0-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="f56a0-110">Comentários podem seguir uma instrução na mesma linha ou ocupar uma linha inteira.</span><span class="sxs-lookup"><span data-stu-id="f56a0-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="f56a0-111">Ambos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="f56a0-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 <span data-ttu-id="f56a0-112">Se seu comentário exigir mais de uma linha, use o símbolo de comentário em cada linha, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="f56a0-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="f56a0-113">Diretrizes de comentários</span><span class="sxs-lookup"><span data-stu-id="f56a0-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="f56a0-114">A tabela a seguir fornece diretrizes gerais para os tipos de comentários que podem preceder uma seção de código.</span><span class="sxs-lookup"><span data-stu-id="f56a0-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="f56a0-115">Esses são sugestões; Visual Basic não impõe regras para adicionar comentários.</span><span class="sxs-lookup"><span data-stu-id="f56a0-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="f56a0-116">Escreva o que funciona melhor, tanto para você quanto para qualquer outra pessoa que leia seu código.</span><span class="sxs-lookup"><span data-stu-id="f56a0-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="f56a0-117">Tipo de comentário</span><span class="sxs-lookup"><span data-stu-id="f56a0-117">Comment type</span></span>|<span data-ttu-id="f56a0-118">Descrição do comentário</span><span class="sxs-lookup"><span data-stu-id="f56a0-118">Comment description</span></span>|  
|<span data-ttu-id="f56a0-119">Finalidade</span><span class="sxs-lookup"><span data-stu-id="f56a0-119">Purpose</span></span>|<span data-ttu-id="f56a0-120">Descreve o que o procedimento faz (não como ele faz)</span><span class="sxs-lookup"><span data-stu-id="f56a0-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="f56a0-121">Suposições</span><span class="sxs-lookup"><span data-stu-id="f56a0-121">Assumptions</span></span>|<span data-ttu-id="f56a0-122">Lista cada variável externa, controle, arquivo aberto ou outro elemento acessado pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="f56a0-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="f56a0-123">Efeitos</span><span class="sxs-lookup"><span data-stu-id="f56a0-123">Effects</span></span>|<span data-ttu-id="f56a0-124">Listas cada variável externa, controle ou arquivo afetado, e o efeito que ele tem (somente se não for óbvio)</span><span class="sxs-lookup"><span data-stu-id="f56a0-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="f56a0-125">Entradas</span><span class="sxs-lookup"><span data-stu-id="f56a0-125">Inputs</span></span>|<span data-ttu-id="f56a0-126">Especifica a finalidade do argumento</span><span class="sxs-lookup"><span data-stu-id="f56a0-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="f56a0-127">Retorna</span><span class="sxs-lookup"><span data-stu-id="f56a0-127">Returns</span></span>|<span data-ttu-id="f56a0-128">Explica os valores retornados pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="f56a0-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="f56a0-129">Lembre-se dos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="f56a0-129">Remember the following points:</span></span>  
  
-   <span data-ttu-id="f56a0-130">Cada declaração de variável importante deve ser precedida por um comentário sobre o uso da variável sendo declarada.</span><span class="sxs-lookup"><span data-stu-id="f56a0-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="f56a0-131">Variáveis, controles e procedimentos devem ser chamados claramente o bastante para que os comentários sejam necessários somente para detalhes de implementação complexos.</span><span class="sxs-lookup"><span data-stu-id="f56a0-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="f56a0-132">Os comentários não podem seguir uma sequência de continuação de linha na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="f56a0-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="f56a0-133">Você pode adicionar ou remover símbolos de comentário de um bloco de código, selecionando uma ou mais linhas de código e escolhendo o **comentário** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) e **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) botões de **editar**  barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="f56a0-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f56a0-134">Você também pode adicionar comentários ao código precedendo o texto com a palavra-chave `REM`.</span><span class="sxs-lookup"><span data-stu-id="f56a0-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="f56a0-135">No entanto, o `'` símbolo e o **comentário**/**Uncomment** botões são mais fáceis de usar e exigem menos espaço e memória.</span><span class="sxs-lookup"><span data-stu-id="f56a0-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f56a0-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f56a0-136">See Also</span></span>  
 [<span data-ttu-id="f56a0-137">Documentando o código com comentários XML</span><span class="sxs-lookup"><span data-stu-id="f56a0-137">Documenting Your Code With XML Comments</span></span>](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [<span data-ttu-id="f56a0-138">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="f56a0-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [<span data-ttu-id="f56a0-139">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f56a0-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [<span data-ttu-id="f56a0-140">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="f56a0-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="f56a0-141">Instrução REM</span><span class="sxs-lookup"><span data-stu-id="f56a0-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
