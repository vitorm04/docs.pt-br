---
title: Variáveis
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: bd6417033a6c2626d17ad003de6c637dd1e8adaa
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91080212"
---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="52b03-102">Variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52b03-102">Variables in Visual Basic</span></span>

<span data-ttu-id="52b03-103">Geralmente, você precisa armazenar valores ao executar cálculos com Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="52b03-103">You often have to store values when you perform calculations with Visual Basic.</span></span> <span data-ttu-id="52b03-104">Por exemplo, talvez você queira calcular vários valores, compará-los e executar operações diferentes dependendo do resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="52b03-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="52b03-105">Você precisará reter os valores se desejar compará-los.</span><span class="sxs-lookup"><span data-stu-id="52b03-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="52b03-106">Uso</span><span class="sxs-lookup"><span data-stu-id="52b03-106">Usage</span></span>  

 <span data-ttu-id="52b03-107">Visual Basic, assim como a maioria das linguagens de programação, usa variáveis para armazenar valores.</span><span class="sxs-lookup"><span data-stu-id="52b03-107">Visual Basic, just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="52b03-108">Uma *variável* tem um nome (a palavra que você usa para se referir ao valor que a variável contém).</span><span class="sxs-lookup"><span data-stu-id="52b03-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="52b03-109">Uma variável também tem um tipo de dados (que determina o tipo de dados que a variável pode armazenar).</span><span class="sxs-lookup"><span data-stu-id="52b03-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="52b03-110">Se precisar armazenar um conjunto indexado de itens de dados estritamente relacionados, uma variável poderá representar uma matriz.</span><span class="sxs-lookup"><span data-stu-id="52b03-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="52b03-111">A inferência de tipo de variável local permite que você declare variáveis sem especificar de maneira explícita um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="52b03-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="52b03-112">Em vez disso, o compilador infere o tipo da variável com base no tipo da expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="52b03-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="52b03-113">Para obter mais informações, consulte [Inferência de tipo de variável local](local-type-inference.md) e [Instrução Option Infer](../../../language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="52b03-113">For more information, see [Local Type Inference](local-type-inference.md) and [Option Infer Statement](../../../language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="52b03-114">Atribuindo valores</span><span class="sxs-lookup"><span data-stu-id="52b03-114">Assigning Values</span></span>  

 <span data-ttu-id="52b03-115">Você pode usar instruções de atribuição para executar cálculos e atribuir o resultado a uma variável, conforme mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="52b03-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> <span data-ttu-id="52b03-116">O sinal de igual (`=`) no exemplo é um operador de atribuição e não um operador de igualdade.</span><span class="sxs-lookup"><span data-stu-id="52b03-116">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="52b03-117">O valor é atribuído à variável `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="52b03-117">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="52b03-118">Para obter mais informações, consulte [Como inserir e remover dados de uma variável](how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="52b03-118">For more information, see [How to: Move Data Into and Out of a Variable](how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="52b03-119">Variáveis e propriedades</span><span class="sxs-lookup"><span data-stu-id="52b03-119">Variables and Properties</span></span>  

 <span data-ttu-id="52b03-120">Como uma variável, uma *propriedade* representa um valor que você pode acessar.</span><span class="sxs-lookup"><span data-stu-id="52b03-120">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="52b03-121">No entanto, ela é mais complexa que uma variável.</span><span class="sxs-lookup"><span data-stu-id="52b03-121">However, it is more complex than a variable.</span></span> <span data-ttu-id="52b03-122">Uma propriedade usa blocos de código que controlam como definir e recuperar seu valor.</span><span class="sxs-lookup"><span data-stu-id="52b03-122">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="52b03-123">Para obter mais informações, consulte [Diferenças entre propriedades e variáveis no Visual Basic](../procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="52b03-123">For more information, see [Differences Between Properties and Variables in Visual Basic](../procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b03-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="52b03-124">See also</span></span>

- [<span data-ttu-id="52b03-125">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="52b03-125">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="52b03-126">Variáveis de Objeto</span><span class="sxs-lookup"><span data-stu-id="52b03-126">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="52b03-127">Solução de problemas de Variáveis</span><span class="sxs-lookup"><span data-stu-id="52b03-127">Troubleshooting Variables</span></span>](troubleshooting-variables.md)
- [<span data-ttu-id="52b03-128">Como inserir e remover dados de uma variável</span><span class="sxs-lookup"><span data-stu-id="52b03-128">How to: Move Data Into and Out of a Variable</span></span>](how-to-move-data-into-and-out-of-a-variable.md)
- [<span data-ttu-id="52b03-129">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="52b03-129">Differences Between Properties and Variables in Visual Basic</span></span>](../procedures/differences-between-properties-and-variables.md)
- [<span data-ttu-id="52b03-130">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="52b03-130">Local Type Inference</span></span>](local-type-inference.md)
