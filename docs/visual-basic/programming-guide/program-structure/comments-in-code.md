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
ms.openlocfilehash: 3635d52532789133a345d9a9228efae869c8c223
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945611"
---
# <a name="comments-in-code-visual-basic"></a><span data-ttu-id="51eba-102">Comentários no código (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51eba-102">Comments in Code (Visual Basic)</span></span>
<span data-ttu-id="51eba-103">À medida que você lê os exemplos de código, você encontra geralmente o símbolo de comentário (`'`).</span><span class="sxs-lookup"><span data-stu-id="51eba-103">As you read the code examples, you often encounter the comment symbol (`'`).</span></span> <span data-ttu-id="51eba-104">Esse símbolo informa o compilador de Visual Basic para ignorar o texto que o segue ou o *Comentário*.</span><span class="sxs-lookup"><span data-stu-id="51eba-104">This symbol tells the Visual Basic compiler to ignore the text following it, or the *comment*.</span></span> <span data-ttu-id="51eba-105">Os comentários são uma breve explicação e/ou anotações adicionadas ao código para o benefício de quem os lê.</span><span class="sxs-lookup"><span data-stu-id="51eba-105">Comments are brief explanatory notes added to code for the benefit of those reading it.</span></span>  
  
 <span data-ttu-id="51eba-106">É uma prática de programação recomendável iniciar todos os procedimentos com um breve comentário descrevendo as características do procedimento e sua funcionalidade (o que ele faz).</span><span class="sxs-lookup"><span data-stu-id="51eba-106">It is good programming practice to begin all procedures with a brief comment describing the functional characteristics of the procedure (what it does).</span></span> <span data-ttu-id="51eba-107">Isso é um benefício para o programador e é vantajoso para qualquer pessoa que examinar o código.</span><span class="sxs-lookup"><span data-stu-id="51eba-107">This is for your own benefit and the benefit of anyone else who examines the code.</span></span> <span data-ttu-id="51eba-108">Você deve separar os detalhes de implementação (como o procedimento faz isso) dos comentários que descrevem as características funcionais.</span><span class="sxs-lookup"><span data-stu-id="51eba-108">You should separate the implementation details (how the procedure does it) from comments that describe the functional characteristics.</span></span> <span data-ttu-id="51eba-109">Quando você incluir detalhes da implementação na descrição, lembre-se de atualizá-los quando você atualizar a função.</span><span class="sxs-lookup"><span data-stu-id="51eba-109">When you include implementation details in the description, remember to update them when you update the function.</span></span>  
  
 <span data-ttu-id="51eba-110">Comentários podem seguir uma instrução na mesma linha ou ocupar uma linha inteira.</span><span class="sxs-lookup"><span data-stu-id="51eba-110">Comments can follow a statement on the same line, or occupy an entire line.</span></span> <span data-ttu-id="51eba-111">Ambos são ilustrados no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="51eba-111">Both are illustrated in the following code.</span></span>  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 <span data-ttu-id="51eba-112">Se seu comentário exigir mais de uma linha, use o símbolo de comentário em cada linha, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="51eba-112">If your comment requires more than one line, use the comment symbol on each line, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a><span data-ttu-id="51eba-113">Diretrizes de comentários</span><span class="sxs-lookup"><span data-stu-id="51eba-113">Commenting Guidelines</span></span>  
 <span data-ttu-id="51eba-114">A tabela a seguir fornece diretrizes gerais para os tipos de comentários que podem preceder uma seção de código.</span><span class="sxs-lookup"><span data-stu-id="51eba-114">The following table provides general guidelines for what types of comments can precede a section of code.</span></span> <span data-ttu-id="51eba-115">Essas são sugestões; Visual Basic não impõe regras para adicionar comentários.</span><span class="sxs-lookup"><span data-stu-id="51eba-115">These are suggestions; Visual Basic does not enforce rules for adding comments.</span></span> <span data-ttu-id="51eba-116">Escreva o que funciona melhor, tanto para você quanto para qualquer outra pessoa que leia seu código.</span><span class="sxs-lookup"><span data-stu-id="51eba-116">Write what works best, both for you and for anyone else who reads your code.</span></span>  
  
|||  
|---|---|  
|<span data-ttu-id="51eba-117">Tipo de comentário</span><span class="sxs-lookup"><span data-stu-id="51eba-117">Comment type</span></span>|<span data-ttu-id="51eba-118">Descrição do comentário</span><span class="sxs-lookup"><span data-stu-id="51eba-118">Comment description</span></span>|  
|<span data-ttu-id="51eba-119">Finalidade</span><span class="sxs-lookup"><span data-stu-id="51eba-119">Purpose</span></span>|<span data-ttu-id="51eba-120">Descreve o que o procedimento faz (não como ele faz)</span><span class="sxs-lookup"><span data-stu-id="51eba-120">Describes what the procedure does (not how it does it)</span></span>|  
|<span data-ttu-id="51eba-121">Suposições</span><span class="sxs-lookup"><span data-stu-id="51eba-121">Assumptions</span></span>|<span data-ttu-id="51eba-122">Lista cada variável externa, controle, arquivo aberto ou outro elemento acessado pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="51eba-122">Lists each external variable, control, open file, or other element accessed by the procedure</span></span>|  
|<span data-ttu-id="51eba-123">Efeitos</span><span class="sxs-lookup"><span data-stu-id="51eba-123">Effects</span></span>|<span data-ttu-id="51eba-124">Listas cada variável externa, controle ou arquivo afetado, e o efeito que ele tem (somente se não for óbvio)</span><span class="sxs-lookup"><span data-stu-id="51eba-124">Lists each affected external variable, control, or file, and the effect it has (only if it is not obvious)</span></span>|  
|<span data-ttu-id="51eba-125">Entradas</span><span class="sxs-lookup"><span data-stu-id="51eba-125">Inputs</span></span>|<span data-ttu-id="51eba-126">Especifica a finalidade do argumento</span><span class="sxs-lookup"><span data-stu-id="51eba-126">Specifies the purpose of the argument</span></span>|  
|<span data-ttu-id="51eba-127">Retorna</span><span class="sxs-lookup"><span data-stu-id="51eba-127">Returns</span></span>|<span data-ttu-id="51eba-128">Explica os valores retornados pelo procedimento</span><span class="sxs-lookup"><span data-stu-id="51eba-128">Explains the values returned by the procedure</span></span>|  
  
 <span data-ttu-id="51eba-129">Lembre-se dos seguintes pontos:</span><span class="sxs-lookup"><span data-stu-id="51eba-129">Remember the following points:</span></span>  
  
- <span data-ttu-id="51eba-130">Cada declaração de variável importante deve ser precedida por um comentário sobre o uso da variável sendo declarada.</span><span class="sxs-lookup"><span data-stu-id="51eba-130">Every important variable declaration should be preceded by a comment describing the use of the variable being declared.</span></span>  
  
- <span data-ttu-id="51eba-131">Variáveis, controles e procedimentos devem ser chamados claramente o bastante para que os comentários sejam necessários somente para detalhes de implementação complexos.</span><span class="sxs-lookup"><span data-stu-id="51eba-131">Variables, controls, and procedures should be named clearly enough that commenting is needed only for complex implementation details.</span></span>  
  
- <span data-ttu-id="51eba-132">Os comentários não podem seguir uma sequência de continuação de linha na mesma linha.</span><span class="sxs-lookup"><span data-stu-id="51eba-132">Comments cannot follow a line-continuation sequence on the same line.</span></span>  
  
 <span data-ttu-id="51eba-133">Você pode adicionar ou remover símbolos de comentário de um bloco de código selecionando uma ou mais linhas de código e escolhendo o comentário![(o botão de Visual Basic comentário](./media/comments-in-code/visual-basic-comment-button.gif)no Visual Studio) e remover os![ **comentários** (o Visual Botão de remover comentário básico no Visual Studio. ) na barra de ferramentas **Editar.** ](./media/comments-in-code/visual-basic-uncomment-button.gif)</span><span class="sxs-lookup"><span data-stu-id="51eba-133">You can add or remove comment symbols for a block of code by selecting one or more lines of code and choosing the **Comment** (![The Visual Basic Comment button in Visual Studio.](./media/comments-in-code/visual-basic-comment-button.gif)) and **Uncomment** (![The Visual Basic Uncomment button in Visual Studio.](./media/comments-in-code/visual-basic-uncomment-button.gif)) buttons on the **Edit** toolbar.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="51eba-134">Você também pode adicionar comentários ao código precedendo o texto com a palavra-chave `REM`.</span><span class="sxs-lookup"><span data-stu-id="51eba-134">You can also add comments to your code by preceding the text with the `REM` keyword.</span></span> <span data-ttu-id="51eba-135">No entanto `'` , o símbolo e os botões de desmarcação de **Comentário**/são mais fáceis de usar e exigem menos espaço e memória.</span><span class="sxs-lookup"><span data-stu-id="51eba-135">However, the `'` symbol and the **Comment**/**Uncomment** buttons are easier to use and require less space and memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51eba-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51eba-136">See also</span></span>

- [<span data-ttu-id="51eba-137">Instintos básicos – documentando seu código com comentários XML</span><span class="sxs-lookup"><span data-stu-id="51eba-137">Basic Instincts - Documenting Your Code With XML Comments</span></span>](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [<span data-ttu-id="51eba-138">Como: Criar documentação XML</span><span class="sxs-lookup"><span data-stu-id="51eba-138">How to: Create XML Documentation</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [<span data-ttu-id="51eba-139">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="51eba-139">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
- [<span data-ttu-id="51eba-140">Estrutura do Programa e Convenções de Código</span><span class="sxs-lookup"><span data-stu-id="51eba-140">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="51eba-141">Instrução REM</span><span class="sxs-lookup"><span data-stu-id="51eba-141">REM Statement</span></span>](../../../visual-basic/language-reference/statements/rem-statement.md)
