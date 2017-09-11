---
title: "Variáveis no Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2fdc670bf4f17000809e75e32c32edb39abf0fed
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="variables-in-visual-basic"></a><span data-ttu-id="b421d-102">Variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b421d-102">Variables in Visual Basic</span></span>
<span data-ttu-id="b421d-103">Você normalmente precisa armazenar valores ao executar cálculos com o [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b421d-103">You often have to store values when you perform calculations with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="b421d-104">Por exemplo, talvez você queira calcular vários valores, compará-los e executar operações diferentes dependendo do resultado da comparação.</span><span class="sxs-lookup"><span data-stu-id="b421d-104">For example, you might want to calculate several values, compare them, and perform different operations on them, depending on the result of the comparison.</span></span> <span data-ttu-id="b421d-105">Você precisará reter os valores se desejar compará-los.</span><span class="sxs-lookup"><span data-stu-id="b421d-105">You have to retain the values if you want to compare them.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="b421d-106">Uso</span><span class="sxs-lookup"><span data-stu-id="b421d-106">Usage</span></span>  
 <span data-ttu-id="b421d-107">O [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], assim como a maioria das linguagens de programação, usa variáveis para armazenar valores.</span><span class="sxs-lookup"><span data-stu-id="b421d-107">[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], just like most programming languages, uses variables for storing values.</span></span> <span data-ttu-id="b421d-108">Uma *variável* tem um nome (a palavra que você usa para se referir ao valor que a variável contém).</span><span class="sxs-lookup"><span data-stu-id="b421d-108">A *variable* has a name (the word that you use to refer to the value that the variable contains).</span></span> <span data-ttu-id="b421d-109">Uma variável também tem um tipo de dados (que determina o tipo de dados que a variável pode armazenar).</span><span class="sxs-lookup"><span data-stu-id="b421d-109">A variable also has a data type (which determines the kind of data that the variable can store).</span></span> <span data-ttu-id="b421d-110">Se precisar armazenar um conjunto indexado de itens de dados estritamente relacionados, uma variável poderá representar uma matriz.</span><span class="sxs-lookup"><span data-stu-id="b421d-110">A variable can represent an array if it has to store an indexed set of closely related data items.</span></span>  
  
 <span data-ttu-id="b421d-111">A inferência de tipo de variável local permite que você declare variáveis sem especificar de maneira explícita um tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="b421d-111">Local type inference enables you to declare variables without explicitly stating a data type.</span></span> <span data-ttu-id="b421d-112">Em vez disso, o compilador infere o tipo da variável com base no tipo da expressão de inicialização.</span><span class="sxs-lookup"><span data-stu-id="b421d-112">Instead, the compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="b421d-113">Para obter mais informações, consulte [Inferência de tipo de variável local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) e [Instrução Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b421d-113">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="assigning-values"></a><span data-ttu-id="b421d-114">Atribuindo valores</span><span class="sxs-lookup"><span data-stu-id="b421d-114">Assigning Values</span></span>  
 <span data-ttu-id="b421d-115">Você pode usar instruções de atribuição para executar cálculos e atribuir o resultado a uma variável, conforme mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b421d-115">You use assignment statements to perform calculations and assign the result to a variable, as the following example shows.</span></span>  
  
 <span data-ttu-id="b421d-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b421d-116">[!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b421d-117">O sinal de igual (`=`) no exemplo é um operador de atribuição e não um operador de igualdade.</span><span class="sxs-lookup"><span data-stu-id="b421d-117">The equal sign (`=`) in this example is an assignment operator, not an equality operator.</span></span> <span data-ttu-id="b421d-118">O valor é atribuído à variável `applesSold`.</span><span class="sxs-lookup"><span data-stu-id="b421d-118">The value is being assigned to the variable `applesSold`.</span></span>  
  
 <span data-ttu-id="b421d-119">Para obter mais informações, consulte [Como inserir e remover dados de uma variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span><span class="sxs-lookup"><span data-stu-id="b421d-119">For more information, see [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).</span></span>  
  
## <a name="variables-and-properties"></a><span data-ttu-id="b421d-120">Variáveis e propriedades</span><span class="sxs-lookup"><span data-stu-id="b421d-120">Variables and Properties</span></span>  
 <span data-ttu-id="b421d-121">Como uma variável, uma *propriedade* representa um valor que você pode acessar.</span><span class="sxs-lookup"><span data-stu-id="b421d-121">Like a variable, a *property* represents a value that you can access.</span></span> <span data-ttu-id="b421d-122">No entanto, ela é mais complexa que uma variável.</span><span class="sxs-lookup"><span data-stu-id="b421d-122">However, it is more complex than a variable.</span></span> <span data-ttu-id="b421d-123">Uma propriedade usa blocos de código que controlam como definir e recuperar seu valor.</span><span class="sxs-lookup"><span data-stu-id="b421d-123">A property uses code blocks that control how to set and retrieve its value.</span></span> <span data-ttu-id="b421d-124">Para obter mais informações, consulte [Diferenças entre propriedades e variáveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="b421d-124">For more information, see [Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b421d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b421d-125">See Also</span></span>  
 <span data-ttu-id="b421d-126">[Declaração de variável](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="b421d-126">[Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
 <span data-ttu-id="b421d-127">[Variáveis de objeto](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b421d-127">[Object Variables](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md) </span></span>  
 <span data-ttu-id="b421d-128">[Solução de problemas de variáveis](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b421d-128">[Troubleshooting Variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md) </span></span>  
 <span data-ttu-id="b421d-129">[Como inserir e remover dados de uma variável](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="b421d-129">[How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
 <span data-ttu-id="b421d-130">[Diferenças entre propriedades e variáveis no Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="b421d-130">[Differences Between Properties and Variables in Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md) </span></span>  
 [<span data-ttu-id="b421d-131">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="b421d-131">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

