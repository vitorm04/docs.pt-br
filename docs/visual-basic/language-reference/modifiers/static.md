---
title: Estático (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e08f46076281e766a5bc0b99cd61fee9cd41ece5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="static-visual-basic"></a><span data-ttu-id="6fc58-102">Estático (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6fc58-102">Static (Visual Basic)</span></span>
<span data-ttu-id="6fc58-103">Especifica que um ou mais variáveis locais declaradas devem continuar a existir e manter seus valores mais recentes após o término do procedimento no qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="6fc58-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fc58-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fc58-104">Remarks</span></span>  
 <span data-ttu-id="6fc58-105">Normalmente, uma variável local em um procedimento deixa de existir assim que o procedimento será interrompida.</span><span class="sxs-lookup"><span data-stu-id="6fc58-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="6fc58-106">Uma variável estática continua existindo e retém seu valor mais recente.</span><span class="sxs-lookup"><span data-stu-id="6fc58-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="6fc58-107">Na próxima vez que seu código chama o procedimento, a variável não for reiniciada, e ela ainda mantém o valor mais recente que você atribuiu a ele.</span><span class="sxs-lookup"><span data-stu-id="6fc58-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="6fc58-108">Uma variável estática continua a existir para o tempo de vida da classe ou módulo que está definido no.</span><span class="sxs-lookup"><span data-stu-id="6fc58-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6fc58-109">Regras</span><span class="sxs-lookup"><span data-stu-id="6fc58-109">Rules</span></span>  
  
-   <span data-ttu-id="6fc58-110">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="6fc58-110">**Declaration Context.**</span></span> <span data-ttu-id="6fc58-111">Você pode usar `Static` somente nas variáveis locais.</span><span class="sxs-lookup"><span data-stu-id="6fc58-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="6fc58-112">Isso significa que o contexto da declaração para um `Static` variável deve ser um procedimento ou um bloco em um procedimento, e ele não pode ser um arquivo de origem, namespace, classe, estrutura ou módulo.</span><span class="sxs-lookup"><span data-stu-id="6fc58-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="6fc58-113">Não é possível usar `Static` dentro de um procedimento de estrutura.</span><span class="sxs-lookup"><span data-stu-id="6fc58-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="6fc58-114">Os tipos de dados de `Static` variáveis locais não podem ser inferidas.</span><span class="sxs-lookup"><span data-stu-id="6fc58-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="6fc58-115">Para obter mais informações, consulte [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="6fc58-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="6fc58-116">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="6fc58-116">**Combined Modifiers.**</span></span> <span data-ttu-id="6fc58-117">Não é possível especificar `Static` junto com `ReadOnly`, `Shadows`, ou `Shared` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="6fc58-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="6fc58-118">Comportamento</span><span class="sxs-lookup"><span data-stu-id="6fc58-118">Behavior</span></span>  
 <span data-ttu-id="6fc58-119">Quando você declara uma variável estática em uma `Shared` procedimento, apenas uma cópia da variável estática está disponível para o aplicativo inteiro.</span><span class="sxs-lookup"><span data-stu-id="6fc58-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="6fc58-120">Você chama um `Shared` nome do procedimento, usando a classe, não uma variável que aponta para uma instância da classe.</span><span class="sxs-lookup"><span data-stu-id="6fc58-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="6fc58-121">Quando você declara uma variável estática em um procedimento que não seja `Shared`, somente uma cópia da variável está disponível para cada instância da classe.</span><span class="sxs-lookup"><span data-stu-id="6fc58-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="6fc58-122">Você pode chamar um procedimento não compartilhado usando uma variável que aponta para uma instância específica da classe.</span><span class="sxs-lookup"><span data-stu-id="6fc58-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6fc58-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fc58-123">Example</span></span>  
 <span data-ttu-id="6fc58-124">O exemplo a seguir demonstra o uso de `Static`.</span><span class="sxs-lookup"><span data-stu-id="6fc58-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="6fc58-125">O `Static` variável `totalSales` foi inicializada para 0 somente uma vez.</span><span class="sxs-lookup"><span data-stu-id="6fc58-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="6fc58-126">Cada vez que você inserir `updateSales`, `totalSales` ainda tem o valor mais recente que você calculou para ela.</span><span class="sxs-lookup"><span data-stu-id="6fc58-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="6fc58-127">O `Static` modificador pode ser usado neste contexto:</span><span class="sxs-lookup"><span data-stu-id="6fc58-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="6fc58-128">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="6fc58-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="6fc58-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fc58-129">See Also</span></span>  
 [<span data-ttu-id="6fc58-130">Sombras</span><span class="sxs-lookup"><span data-stu-id="6fc58-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="6fc58-131">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="6fc58-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="6fc58-132">Tempo de vida no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6fc58-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="6fc58-133">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="6fc58-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="6fc58-134">Estruturas</span><span class="sxs-lookup"><span data-stu-id="6fc58-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="6fc58-135">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="6fc58-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="6fc58-136">Objetos e Classes</span><span class="sxs-lookup"><span data-stu-id="6fc58-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
