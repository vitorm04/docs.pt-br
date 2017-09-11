---
title: "Como: Declarar enumerações (Visual Basic) | Documentos do Microsoft"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
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
ms.openlocfilehash: 7adaca7e7252ce7165a5fd27b5bc9c049388206c
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="014e7-102">Como declarar enumerações (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="014e7-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="014e7-103">Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou módulo.</span><span class="sxs-lookup"><span data-stu-id="014e7-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="014e7-104">Você não pode declarar uma enumeração dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="014e7-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="014e7-105">Para especificar o nível apropriado de acesso, use `Private`, `Protected`, `Friend`, ou `Public`.</span><span class="sxs-lookup"><span data-stu-id="014e7-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="014e7-106">Um `Enum` tipo tem um nome, um tipo subjacente e um conjunto de campos, cada um representando uma constante.</span><span class="sxs-lookup"><span data-stu-id="014e7-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="014e7-107">O nome deve ser válido [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualificador.</span><span class="sxs-lookup"><span data-stu-id="014e7-107">The name must be a valid [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualifier.</span></span> <span data-ttu-id="014e7-108">O tipo subjacente deve ser um dos tipos inteiros —`Byte`, `Short`, `Long` ou `Integer`.</span><span class="sxs-lookup"><span data-stu-id="014e7-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="014e7-109">`Integer` é o padrão.</span><span class="sxs-lookup"><span data-stu-id="014e7-109">`Integer` is the default.</span></span> <span data-ttu-id="014e7-110">Enumerações são sempre fortemente tipadas e não são intercambiáveis com tipos de número inteiro.</span><span class="sxs-lookup"><span data-stu-id="014e7-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="014e7-111">Enumerações não podem ter valores de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="014e7-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="014e7-112">Se uma enumeração é atribuída um valor de ponto flutuante com `Option Strict On`, um erro de compilação acontece.</span><span class="sxs-lookup"><span data-stu-id="014e7-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="014e7-113">Se `Option Strict` é `Off`, o valor é convertido automaticamente para o `Enum` tipo.</span><span class="sxs-lookup"><span data-stu-id="014e7-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="014e7-114">Para obter informações sobre nomes e como usar o `Imports` instrução para tornar a qualificação de nome desnecessário, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="014e7-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="014e7-115">Para declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="014e7-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="014e7-116">Escrever uma declaração que inclua um nível de acesso de código, o `Enum` palavra-chave e um nome válido, como os exemplos a seguir, cada uma das quais declara um outro `Enum`.</span><span class="sxs-lookup"><span data-stu-id="014e7-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     <span data-ttu-id="014e7-117">[!code-vb[VbEnumsTask n º&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="014e7-117">[!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span></span>  
  
2.  <span data-ttu-id="014e7-118">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="014e7-118">Define the constants in the enumeration.</span></span> <span data-ttu-id="014e7-119">Por padrão, a primeira constante em uma enumeração é inicializada para `0`, e constantes subsequentes são inicializados com um valor de um mais do que a constante anterior.</span><span class="sxs-lookup"><span data-stu-id="014e7-119">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="014e7-120">Por exemplo, a enumeração seguir `Days`, contém uma constante chamada `Sunday` com o valor `0`, uma constante chamada `Monday` com o valor `1`, uma constante chamada `Tuesday` com o valor de `2`, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="014e7-120">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     <span data-ttu-id="014e7-121">[!code-vb[VbEnumsTask n º&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="014e7-121">[!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span></span>  
  
3.  <span data-ttu-id="014e7-122">Você pode explicitamente atribuir valores às constantes em uma enumeração usando uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="014e7-122">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="014e7-123">Você pode atribuir qualquer valor inteiro, incluindo os números negativos.</span><span class="sxs-lookup"><span data-stu-id="014e7-123">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="014e7-124">Por exemplo, convém constantes com valores menores que zero para representar condições de erro.</span><span class="sxs-lookup"><span data-stu-id="014e7-124">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="014e7-125">Na enumeração seguir, a constante `Invalid` explicitamente é atribuído o valor `–1`e a constante `Sunday` é atribuído o valor `0`.</span><span class="sxs-lookup"><span data-stu-id="014e7-125">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="014e7-126">Porque é a primeira constante na enumeração, `Saturday` também é inicializada com o valor `0`.</span><span class="sxs-lookup"><span data-stu-id="014e7-126">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="014e7-127">O valor de `Monday` é `1` (mais do que o valor de `Sunday`); o valor de `Tuesday` é `2`, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="014e7-127">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     <span data-ttu-id="014e7-128">[!code-vb[VbEnumsTask n º&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="014e7-128">[!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span></span>  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="014e7-129">Para declarar uma enumeração como um tipo explícito</span><span class="sxs-lookup"><span data-stu-id="014e7-129">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="014e7-130">Especifique o tipo de enumeração usando o `As` cláusula, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="014e7-130">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     <span data-ttu-id="014e7-131">[!code-vb[VbEnumsTask n º&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="014e7-131">[!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="014e7-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="014e7-132">See Also</span></span>  
 <span data-ttu-id="014e7-133">[Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-133">[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="014e7-134"> [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-134"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="014e7-135"> [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-135"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="014e7-136"> [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-136"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="014e7-137"> [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-137"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="014e7-138"> [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-138"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="014e7-139"> [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="014e7-139"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="014e7-140"> [Constantes e Enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="014e7-140"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
