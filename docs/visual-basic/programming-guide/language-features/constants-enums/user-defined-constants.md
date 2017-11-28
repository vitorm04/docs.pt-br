---
title: "Constantes definidas pelo usuário (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce839c3e843a52b31e40c13cb765f8eaf9959ea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="d26ff-102">Constantes definidas pelo usuário (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d26ff-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="d26ff-103">Uma constante é um nome significativo que toma o lugar de um número ou uma cadeia de caracteres que não é alterado.</span><span class="sxs-lookup"><span data-stu-id="d26ff-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="d26ff-104">Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d26ff-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="d26ff-105">Você pode usar constantes definidas por controles ou componentes que você trabalha com, ou você pode criar seus próprios.</span><span class="sxs-lookup"><span data-stu-id="d26ff-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="d26ff-106">Constantes que você mesmo cria são descritas como *definida pelo usuário*.</span><span class="sxs-lookup"><span data-stu-id="d26ff-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="d26ff-107">Declarar uma constante com o `Const` instrução, usando as mesmas diretrizes que você faria para criar um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="d26ff-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="d26ff-108">Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.</span><span class="sxs-lookup"><span data-stu-id="d26ff-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="d26ff-109">Uso da instrução Const</span><span class="sxs-lookup"><span data-stu-id="d26ff-109">Const Statement Usage</span></span>  
 <span data-ttu-id="d26ff-110">Um `Const` instrução pode representar um matemática ou quantidade de data/hora:</span><span class="sxs-lookup"><span data-stu-id="d26ff-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]  
  
 <span data-ttu-id="d26ff-111">Ele também pode definir `String` constantes:</span><span class="sxs-lookup"><span data-stu-id="d26ff-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]  
  
 <span data-ttu-id="d26ff-112">A expressão à direita do sinal de igual ( `=` ) geralmente é um número ou cadeia de caracteres literal, mas também pode ser uma expressão que resulta em um número ou uma cadeia de caracteres (embora essa expressão não pode conter chamadas a funções).</span><span class="sxs-lookup"><span data-stu-id="d26ff-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="d26ff-113">Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:</span><span class="sxs-lookup"><span data-stu-id="d26ff-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="d26ff-114">Escopo de constantes definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="d26ff-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="d26ff-115">Um `Const` escopo da instrução é o mesmo que uma variável declarada no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="d26ff-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="d26ff-116">Você pode especificar o escopo em qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="d26ff-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="d26ff-117">Para criar uma constante que existe somente dentro de um procedimento, declare-o dentro desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="d26ff-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="d26ff-118">Para criar uma constante disponível para todos os procedimentos dentro de uma classe, mas não para qualquer código fora desse módulo, declare-o na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="d26ff-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="d26ff-119">Para criar uma constante que está disponível para todos os membros de um assembly, mas não para clientes fora do assembly, declare-o usando o `Friend` palavra-chave na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="d26ff-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="d26ff-120">Para criar uma constante disponível em todo o aplicativo, declare-o usando o `Public` seção de palavra-chave nas declarações de classe.</span><span class="sxs-lookup"><span data-stu-id="d26ff-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="d26ff-121">Para obter mais informações, consulte [como: declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="d26ff-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="d26ff-122">Evitar referências circulares</span><span class="sxs-lookup"><span data-stu-id="d26ff-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="d26ff-123">Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo*, ou uma referência circular, entre duas ou mais constantes.</span><span class="sxs-lookup"><span data-stu-id="d26ff-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="d26ff-124">Um ciclo ocorre quando você tiver duas ou mais constantes públicas, cada uma delas é definida em termos de outros, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d26ff-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]  
[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]  
  
 <span data-ttu-id="d26ff-125">Se ocorrer um ciclo, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="d26ff-125">If a cycle occurs, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d26ff-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d26ff-126">See Also</span></span>  
 [<span data-ttu-id="d26ff-127">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="d26ff-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="d26ff-128">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="d26ff-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="d26ff-129">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="d26ff-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)  
 [<span data-ttu-id="d26ff-130">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="d26ff-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [<span data-ttu-id="d26ff-131">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="d26ff-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [<span data-ttu-id="d26ff-132">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="d26ff-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="d26ff-133">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="d26ff-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="d26ff-134">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="d26ff-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="d26ff-135">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="d26ff-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
