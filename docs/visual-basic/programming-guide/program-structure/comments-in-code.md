---
title: "Comentários no código (Visual Basic) | Documentos do Microsoft"
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
- Uncomment button
- REM statement
- comments, in code
- comments, Visual Basic code
- Comment button
- buttons, Uncomment
- buttons, Comment
- code comments, Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
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
ms.openlocfilehash: e872c9bb67835573aadcc1016f2c6a98d434201e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="24e19-102">Comentários no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24e19-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="24e19-103">À medida que você lê os exemplos de código, você encontra geralmente o símbolo de comentário (`'`).</span><span class="sxs-lookup"><span data-stu-id="24e19-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="24e19-104">Esse símbolo informa o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador ignore o texto a seguir, ou o *comentário*.</span><span class="sxs-lookup"><span data-stu-id="24e19-104">This symbol tells the [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="24e19-105">Os comentários são uma breve explicação e/ou anotações adicionadas ao código para o benefício de quem os lê.</span><span class="sxs-lookup"><span data-stu-id="24e19-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="24e19-106">É uma prática de programação recomendável iniciar todos os procedimentos com um breve comentário descrevendo as características do procedimento e sua funcionalidade (o que ele faz).</span><span class="sxs-lookup"><span data-stu-id="24e19-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="24e19-107">Isso é um benefício para o programador e é vantajoso para qualquer pessoa que examinar o código.</span><span class="sxs-lookup"><span data-stu-id="24e19-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="24e19-108">Você deve separar os detalhes de implementação (como o procedimento faz isso) dos comentários que descrevem as características funcionais.</span><span class="sxs-lookup"><span data-stu-id="24e19-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="24e19-109">Quando você incluir detalhes da implementação na descrição, lembre-se de atualizá-los quando você atualizar a função.</span><span class="sxs-lookup"><span data-stu-id="24e19-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="24e19-110">Comentários podem seguir uma instrução na mesma linha ou ocupar uma linha inteira.</span><span class="sxs-lookup"><span data-stu-id="24e19-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="24e19-111">Ambos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="24e19-111">Both are illustrated in the following code.</span></span>  
  
 <span data-ttu-id="24e19-112">[!code-vb[VbVbcnConventions n º&16;](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="24e19-112">[!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]</span></span>  
  
 <span data-ttu-id="24e19-113">Se seu comentário exigir mais de uma linha, use o símbolo de comentário em cada linha, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="24e19-113">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 <span data-ttu-id="24e19-114">[!code-vb[17 VbVbcnConventions](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="24e19-114">[!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]</span></span>  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="24e19-115">Diretrizes de comentários</span><span class="sxs-lookup"><span data-stu-id="24e19-115">Commenting Guidelines</span></span>  
 <span data-ttu-id="24e19-116">A tabela a seguir fornece diretrizes gerais para os tipos de comentários que podem preceder uma seção de código.</span><span class="sxs-lookup"><span data-stu-id="24e19-116">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="24e19-117">São sugestões; o [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] não impõe regras para adicionar comentários.</span><span class="sxs-lookup"><span data-stu-id="24e19-117">These are suggestions; [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] does not enforce rules for adding comments.</span></span> <span data-ttu-id="24e19-118">Escreva o que funciona melhor, tanto para você quanto para qualquer outra pessoa que leia seu código.</span><span class="sxs-lookup"><span data-stu-id="24e19-118">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="24e19-119">Tipo de comentário</span><span class="sxs-lookup"><span data-stu-id="24e19-119">Comment type</span></span>|<span data-ttu-id="24e19-120">Descrição do comentário</span><span class="sxs-lookup"><span data-stu-id="24e19-120">Comment description</span></span>|  
|<span data-ttu-id="24e19-121">Finalidade</span><span class="sxs-lookup"><span data-stu-id="24e19-121">Purpose</span></span>|<span data-ttu-id="24e19-122">Descreve o que o procedimento faz (não como ele faz)</span><span class="sxs-lookup"><span data-stu-id="24e19-122">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="24e19-123">Suposições</span><span class="sxs-lookup"><span data-stu-id="24e19-123">Assumptions</span></span>|<span data-ttu-id="24e19-124">Lista cada variável externa, controle, arquivo aberto ou outro elemento acessado pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="24e19-124">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="24e19-125">Efeitos</span><span class="sxs-lookup"><span data-stu-id="24e19-125">Effects</span></span>|<span data-ttu-id="24e19-126">Listas cada variável externa, controle ou arquivo afetado, e o efeito que ele tem (somente se não for óbvio)</span><span class="sxs-lookup"><span data-stu-id="24e19-126">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="24e19-127">Entradas</span><span class="sxs-lookup"><span data-stu-id="24e19-127">Inputs</span></span>|<span data-ttu-id="24e19-128">Especifica a finalidade do argumento</span><span class="sxs-lookup"><span data-stu-id="24e19-128">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="24e19-129">Retorna</span><span class="sxs-lookup"><span data-stu-id="24e19-129">Returns</span></span>|<span data-ttu-id="24e19-130">Explica os valores retornados pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="24e19-130">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="24e19-131">Lembre-se dos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="24e19-131">Remember the following points:</span></span>  
  
-   <span data-ttu-id="24e19-132">Cada declaração de variável importante deve ser precedida por um comentário sobre o uso da variável sendo declarada.</span><span class="sxs-lookup"><span data-stu-id="24e19-132">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
-   <span data-ttu-id="24e19-133">Variáveis, controles e procedimentos devem ser chamados claramente o bastante para que os comentários sejam necessários somente para detalhes de implementação complexos.</span><span class="sxs-lookup"><span data-stu-id="24e19-133">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
-   <span data-ttu-id="24e19-134">Os comentários não podem seguir uma sequência de continuação de linha na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="24e19-134">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="24e19-135">Você pode adicionar ou remover símbolos de comentário de um bloco de código, selecionando uma ou mais linhas de código e escolhendo o **comentário** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) e **Remover comentário** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) botões de **editar** barra de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="24e19-135">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton")) and **Uncomment** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24e19-136">Você também pode adicionar comentários ao código precedendo o texto com a palavra-chave `REM`.</span><span class="sxs-lookup"><span data-stu-id="24e19-136">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="24e19-137">No entanto, o `'` símbolo e o **comentário**/**Remover comentário** botões são mais fáceis de usar e exigem menos espaço e memória.</span><span class="sxs-lookup"><span data-stu-id="24e19-137">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e19-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24e19-138">See Also</span></span>  
 <span data-ttu-id="24e19-139">[Documentando o código com comentários XML](http://msdn.microsoft.com/magazine/dd722812.aspx) </span><span class="sxs-lookup"><span data-stu-id="24e19-139">[Documenting Your Code With XML Comments](http://msdn.microsoft.com/magazine/dd722812.aspx) </span></span>  
<span data-ttu-id="24e19-140"> [Como: criar documentação XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span><span class="sxs-lookup"><span data-stu-id="24e19-140"> [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md) </span></span>  
<span data-ttu-id="24e19-141"> [Marcas de comentário XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span><span class="sxs-lookup"><span data-stu-id="24e19-141"> [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md) </span></span>  
<span data-ttu-id="24e19-142"> [Estrutura do programa e convenções de código](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="24e19-142"> [Program Structure and Code Conventions](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md) </span></span>  
<span data-ttu-id="24e19-143"> [Instrução REM](../../../visual-basic/language-reference/statements/rem-statement.md)</span><span class="sxs-lookup"><span data-stu-id="24e19-143"> [REM Statement](../../../visual-basic/language-reference/statements/rem-statement.md)</span></span>
