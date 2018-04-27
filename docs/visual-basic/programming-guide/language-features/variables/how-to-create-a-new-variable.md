---
title: Como criar uma nova variável (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aff160584d3d1fe382020d5b8c25ac57dab66d92
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-a-new-variable-visual-basic"></a><span data-ttu-id="6003e-102">Como criar uma nova variável (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6003e-102">How to: Create a New Variable (Visual Basic)</span></span>
<span data-ttu-id="6003e-103">Crie uma variável com um [instrução Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6003e-103">You create a variable with a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
### <a name="to-create-a-new-variable"></a><span data-ttu-id="6003e-104">Para criar uma nova variável</span><span class="sxs-lookup"><span data-stu-id="6003e-104">To create a new variable</span></span>  
  
1.  <span data-ttu-id="6003e-105">Declare a variável em uma `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="6003e-105">Declare the variable in a `Dim` statement.</span></span>  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  <span data-ttu-id="6003e-106">Incluir as especificações para as características da variável, como [privada](../../../../visual-basic/language-reference/modifiers/private.md), [estático](../../../../visual-basic/language-reference/modifiers/static.md), [sombras](../../../../visual-basic/language-reference/modifiers/shadows.md), ou [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="6003e-106">Include specifications for the variable's characteristics, such as [Private](../../../../visual-basic/language-reference/modifiers/private.md), [Static](../../../../visual-basic/language-reference/modifiers/static.md), [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md), or [WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md).</span></span> <span data-ttu-id="6003e-107">Para obter mais informações, consulte [características do elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span><span class="sxs-lookup"><span data-stu-id="6003e-107">For more information, see [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
     <span data-ttu-id="6003e-108">Não é necessário o `Dim` palavra-chave se você usar outras palavras-chave na declaração.</span><span class="sxs-lookup"><span data-stu-id="6003e-108">You do not need the `Dim` keyword if you use other keywords in the declaration.</span></span>  
  
3.  <span data-ttu-id="6003e-109">Siga as especificações com o nome da variável, que deve seguir as convenções e regras do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6003e-109">Follow the specifications with the variable's name, which must follow Visual Basic rules and conventions.</span></span> <span data-ttu-id="6003e-110">Para obter mais informações, consulte [nomes de elemento declarado](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6003e-110">For more information, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  <span data-ttu-id="6003e-111">Siga o nome com o [como](../../../../visual-basic/language-reference/statements/as-clause.md) cláusula para especificar o tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="6003e-111">Follow the name with the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause to specify the variable's data type.</span></span>  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     <span data-ttu-id="6003e-112">Se você não especificar o tipo de dados, ele usa o padrão: `Object`.</span><span class="sxs-lookup"><span data-stu-id="6003e-112">If you do not specify the data type, it uses the default: `Object`.</span></span>  
  
5.  <span data-ttu-id="6003e-113">Siga o `As` cláusula com um sinal de igual (`=`) e siga o sinal de igualdade com o valor da variável inicial.</span><span class="sxs-lookup"><span data-stu-id="6003e-113">Follow the `As` clause with an equal sign (`=`) and follow the equal sign with the variable's initial value.</span></span>  
  
     <span data-ttu-id="6003e-114">Visual Basic atribui o valor especificado para a variável sempre que ele executa o `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="6003e-114">Visual Basic assigns the specified value to the variable every time it runs the `Dim` statement.</span></span> <span data-ttu-id="6003e-115">Se você não especificar um valor inicial, o Visual Basic atribui o valor inicial padrão para o tipo de dados quando ele entra pela primeira vez o código que contém o `Dim` instrução.</span><span class="sxs-lookup"><span data-stu-id="6003e-115">If you do not specify an initial value, Visual Basic assigns the default initial value for the variable's data type when it first enters the code that contains the `Dim` statement.</span></span>  
  
     <span data-ttu-id="6003e-116">Se a variável é um tipo de referência, você pode criar uma instância de sua classe, incluindo o [novo operador](../../../../visual-basic/language-reference/operators/new-operator.md) palavra-chave no `As` cláusula.</span><span class="sxs-lookup"><span data-stu-id="6003e-116">If the variable is a reference type, you can create an instance of its class by including the [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) keyword in the `As` clause.</span></span> <span data-ttu-id="6003e-117">Se você não usar `New`, o valor inicial da variável é [nada](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="6003e-117">If you do not use `New`, the initial value of the variable is [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="6003e-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6003e-118">See Also</span></span>  
 [<span data-ttu-id="6003e-119">Variáveis</span><span class="sxs-lookup"><span data-stu-id="6003e-119">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="6003e-120">Declaração de Variável</span><span class="sxs-lookup"><span data-stu-id="6003e-120">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="6003e-121">Nomes de Elementos Declarados</span><span class="sxs-lookup"><span data-stu-id="6003e-121">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="6003e-122">Características do Elemento Declarado</span><span class="sxs-lookup"><span data-stu-id="6003e-122">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="6003e-123">Tipos de Valor e Tipos de Referência</span><span class="sxs-lookup"><span data-stu-id="6003e-123">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="6003e-124">Instruções</span><span class="sxs-lookup"><span data-stu-id="6003e-124">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)  
 [<span data-ttu-id="6003e-125">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="6003e-125">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="6003e-126">Instrução Option Infer</span><span class="sxs-lookup"><span data-stu-id="6003e-126">Option Infer Statement</span></span>](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
