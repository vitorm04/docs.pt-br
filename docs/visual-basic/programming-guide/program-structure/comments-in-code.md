---
title: Comentários no código
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
ms.openlocfilehash: b50e76b8f832c3a214ca54f97bab8b0b6789ac25
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403311"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="03a02-102">Comentários no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03a02-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="03a02-103">À medida que você lê os exemplos de código, você encontra geralmente o símbolo de comentário (`'`).</span><span class="sxs-lookup"><span data-stu-id="03a02-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="03a02-104">Esse símbolo informa o compilador de Visual Basic para ignorar o texto que o segue ou o *Comentário*.</span><span class="sxs-lookup"><span data-stu-id="03a02-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="03a02-105">Os comentários são uma breve explicação e/ou anotações adicionadas ao código para o benefício de quem os lê.</span><span class="sxs-lookup"><span data-stu-id="03a02-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="03a02-106">É uma prática de programação recomendável iniciar todos os procedimentos com um breve comentário descrevendo as características do procedimento e sua funcionalidade (o que ele faz).</span><span class="sxs-lookup"><span data-stu-id="03a02-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="03a02-107">Isso é um benefício para o programador e é vantajoso para qualquer pessoa que examinar o código.</span><span class="sxs-lookup"><span data-stu-id="03a02-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="03a02-108">Você deve separar os detalhes de implementação (como o procedimento faz isso) dos comentários que descrevem as características funcionais.</span><span class="sxs-lookup"><span data-stu-id="03a02-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="03a02-109">Quando você incluir detalhes da implementação na descrição, lembre-se de atualizá-los quando você atualizar a função.</span><span class="sxs-lookup"><span data-stu-id="03a02-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="03a02-110">Comentários podem seguir uma instrução na mesma linha ou ocupar uma linha inteira.</span><span class="sxs-lookup"><span data-stu-id="03a02-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="03a02-111">Ambos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="03a02-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="03a02-112">Se seu comentário exigir mais de uma linha, use o símbolo de comentário em cada linha, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="03a02-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="03a02-113">Diretrizes de comentários</span><span class="sxs-lookup"><span data-stu-id="03a02-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="03a02-114">A tabela a seguir fornece diretrizes gerais para os tipos de comentários que podem preceder uma seção de código.</span><span class="sxs-lookup"><span data-stu-id="03a02-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="03a02-115">Essas são sugestões; Visual Basic não impõe regras para adicionar comentários.</span><span class="sxs-lookup"><span data-stu-id="03a02-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="03a02-116">Escreva o que funciona melhor, tanto para você quanto para qualquer outra pessoa que leia seu código.</span><span class="sxs-lookup"><span data-stu-id="03a02-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="03a02-117">Tipo de comentário</span><span class="sxs-lookup"><span data-stu-id="03a02-117">Comment type</span></span>|<span data-ttu-id="03a02-118">Descrição do comentário</span><span class="sxs-lookup"><span data-stu-id="03a02-118">Comment description</span></span>|  
|<span data-ttu-id="03a02-119">Finalidade</span><span class="sxs-lookup"><span data-stu-id="03a02-119">Purpose</span></span>|<span data-ttu-id="03a02-120">Descreve o que o procedimento faz (não como ele faz)</span><span class="sxs-lookup"><span data-stu-id="03a02-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="03a02-121">Suposições</span><span class="sxs-lookup"><span data-stu-id="03a02-121">Assumptions</span></span>|<span data-ttu-id="03a02-122">Lista cada variável externa, controle, arquivo aberto ou outro elemento acessado pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="03a02-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="03a02-123">Efeitos</span><span class="sxs-lookup"><span data-stu-id="03a02-123">Effects</span></span>|<span data-ttu-id="03a02-124">Listas cada variável externa, controle ou arquivo afetado, e o efeito que ele tem (somente se não for óbvio)</span><span class="sxs-lookup"><span data-stu-id="03a02-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="03a02-125">Entradas</span><span class="sxs-lookup"><span data-stu-id="03a02-125">Inputs</span></span>|<span data-ttu-id="03a02-126">Especifica a finalidade do argumento</span><span class="sxs-lookup"><span data-stu-id="03a02-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="03a02-127">Retornos</span><span class="sxs-lookup"><span data-stu-id="03a02-127">Returns</span></span>|<span data-ttu-id="03a02-128">Explica os valores retornados pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="03a02-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="03a02-129">Lembre-se dos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="03a02-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="03a02-130">Cada declaração de variável importante deve ser precedida por um comentário sobre o uso da variável sendo declarada.</span><span class="sxs-lookup"><span data-stu-id="03a02-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="03a02-131">Variáveis, controles e procedimentos devem ser chamados claramente o bastante para que os comentários sejam necessários somente para detalhes de implementação complexos.</span><span class="sxs-lookup"><span data-stu-id="03a02-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="03a02-132">Os comentários não podem seguir uma sequência de continuação de linha na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="03a02-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="03a02-133">Você pode adicionar ou remover símbolos de comentário de um bloco de código selecionando uma ou mais linhas de código e escolhendo o **Comentário** ( ![ o botão de Visual Basic comentário no Visual Studio ](./media/comments-in-code/visual-basic-comment-button.gif) ) e remover os **comentários** ( ![ o botão Visual Basic remover comentários no Visual Studio. ](./media/comments-in-code/visual-basic-uncomment-button.gif) ) na barra de ferramentas **Editar** .</span><span class="sxs-lookup"><span data-stu-id="03a02-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03a02-134">Você também pode adicionar comentários ao código precedendo o texto com a palavra-chave `REM`.</span><span class="sxs-lookup"><span data-stu-id="03a02-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="03a02-135">No entanto, o `'` símbolo e os botões de desmarcação de **Comentário** / **Uncomment** são mais fáceis de usar e exigem menos espaço e memória.</span><span class="sxs-lookup"><span data-stu-id="03a02-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03a02-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="03a02-136">See also</span></span>

- [<span data-ttu-id="03a02-137">Instintos básicos – documentando seu código com comentários XML</span><span class="sxs-lookup"><span data-stu-id="03a02-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](https://docs.microsoft.com/archive/msdn-magazine/2009/may/documenting-your-code-with-xml-comments)
- [<span data-ttu-id="03a02-138">Como criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="03a02-138">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
- [<span data-ttu-id="03a02-139">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="03a02-139">XML Comment Tags</span></span>](../../language-reference/xmldoc/index.md)
- [<span data-ttu-id="03a02-140">Estrutura do programa e convenções de código</span><span class="sxs-lookup"><span data-stu-id="03a02-140">Program Structure and Code Conventions</span></span>](program-structure-and-code-conventions.md)
- [<span data-ttu-id="03a02-141">Instrução REM</span><span class="sxs-lookup"><span data-stu-id="03a02-141">REM Statement</span></span>](../../language-reference/statements/rem-statement.md)
