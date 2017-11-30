---
title: "Como declarar enumerações (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 938550ebbfcf099729db3de96b809549cb234d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="0d7ae-102">Como declarar enumerações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d7ae-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="0d7ae-103">Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="0d7ae-104">Você não pode declarar uma enumeração dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="0d7ae-105">Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`, ou `Public`.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="0d7ae-106">Um `Enum` tipo tem um nome, um tipo subjacente e um conjunto de campos, cada uma representando uma constante.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="0d7ae-107">O nome deve ser um qualificador válido do Visual Basic .NET.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="0d7ae-108">O tipo subjacente deve ser um dos tipos de inteiro —`Byte`, `Short`, `Long` ou `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="0d7ae-109">`Integer` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-109">`Integer` is the default.</span></span> <span data-ttu-id="0d7ae-110">Enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de número inteiro.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="0d7ae-111">Enumerações não podem ter valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="0d7ae-112">Se uma enumeração é atribuída um valor de ponto flutuante com `Option Strict On`, um erro de compilação acontece.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="0d7ae-113">Se `Option Strict` é `Off`, o valor é convertido automaticamente para o `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="0d7ae-114">Para obter informações sobre nomes e como usar o `Imports` instrução para garantir a qualificação de nome desnecessário, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="0d7ae-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="0d7ae-115">Para declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="0d7ae-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="0d7ae-116">Escreva uma declaração que inclui um nível de acesso do código, o `Enum` palavra-chave e um nome válido, como nos exemplos a seguir, cada uma delas declara outra `Enum`.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  <span data-ttu-id="0d7ae-117">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="0d7ae-118">Por padrão, a primeira constante em uma enumeração é inicializada como `0`, e as constantes subsequentes são inicializadas com um valor de constante anterior mais um.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="0d7ae-119">Por exemplo, a enumeração seguir `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor de `2`, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  <span data-ttu-id="0d7ae-120">Explicitamente, você pode atribuir valores às constantes em uma enumeração usando uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="0d7ae-121">Você pode atribuir qualquer valor inteiro, incluindo números negativos.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="0d7ae-122">Por exemplo, talvez você queira constantes com valores menores que zero para representar condições de erro.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="0d7ae-123">Na enumeração seguir, a constante `Invalid` explicitamente atribuído o valor `–1`e a constante `Sunday` é atribuído o valor `0`.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="0d7ae-124">Porque é a primeira constante na enumeração, `Saturday` também é inicializada com o valor `0`.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="0d7ae-125">O valor de `Monday` é `1` (mais do que o valor de um `Sunday`); o valor de `Tuesday` é `2`, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="0d7ae-126">Para declarar uma enumeração como um tipo explícito</span><span class="sxs-lookup"><span data-stu-id="0d7ae-126">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="0d7ae-127">Especifique o tipo de enum usando o `As` cláusula, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0d7ae-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0d7ae-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d7ae-128">See Also</span></span>  
 [<span data-ttu-id="0d7ae-129">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="0d7ae-129">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="0d7ae-130">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="0d7ae-130">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="0d7ae-131">Como: iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d7ae-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="0d7ae-132">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="0d7ae-132">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="0d7ae-133">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="0d7ae-133">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="0d7ae-134">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="0d7ae-134">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="0d7ae-135">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="0d7ae-135">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="0d7ae-136">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="0d7ae-136">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
