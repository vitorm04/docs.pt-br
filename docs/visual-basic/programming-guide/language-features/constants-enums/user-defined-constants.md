---
title: Constantes definidas pelo usuário (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: e519fcaf90c6f18e75d5c409cbe7067d5db36429
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975934"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="1d4c1-102">Constantes definidas pelo usuário (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d4c1-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="1d4c1-103">Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="1d4c1-104">Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="1d4c1-105">Você pode usar constantes que são definidas por controles ou componentes que funcionam com, ou você pode criar seus próprios.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="1d4c1-106">Constantes que você mesmo cria são descritas como *definidos pelo usuário*.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="1d4c1-107">Declarar uma constante com o `Const` instrução, usando as mesmas diretrizes que você faria para a criação de um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="1d4c1-108">Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="1d4c1-109">Uso da instrução Const</span><span class="sxs-lookup"><span data-stu-id="1d4c1-109">Const Statement Usage</span></span>  
 <span data-ttu-id="1d4c1-110">Um `Const` declaração pode representar uma matemática ou quantidade de data/hora:</span><span class="sxs-lookup"><span data-stu-id="1d4c1-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="1d4c1-111">Ele também pode definir `String` constantes:</span><span class="sxs-lookup"><span data-stu-id="1d4c1-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="1d4c1-112">A expressão no lado direito do sinal de igual ( `=` ) costuma ser um número ou cadeia de caracteres literal, mas também pode ser uma expressão que resulta em um número ou cadeia de caracteres (embora essa expressão não pode conter chamadas a funções).</span><span class="sxs-lookup"><span data-stu-id="1d4c1-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="1d4c1-113">Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:</span><span class="sxs-lookup"><span data-stu-id="1d4c1-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="1d4c1-114">Escopo das constantes definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="1d4c1-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="1d4c1-115">Um `Const` escopo da instrução é a mesma de uma variável declarada no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="1d4c1-116">Você pode especificar o escopo em qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="1d4c1-116">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="1d4c1-117">Para criar uma constante que existe somente dentro de um procedimento, declare-o dentro desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="1d4c1-118">Para criar uma constante disponível para todos os procedimentos dentro de uma classe, mas não para qualquer código fora desse módulo, declare-o na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="1d4c1-119">Para criar uma constante que está disponível para todos os membros de um assembly, mas não para clientes fora do assembly, declare-o usando o `Friend` palavra-chave na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="1d4c1-120">Para criar uma constante disponível em todo o aplicativo, declare-o usando o `Public` seção de palavra-chave nas declarações de classe.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="1d4c1-121">Para obter mais informações, confira [Como: Declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="1d4c1-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="1d4c1-122">Evitar referências circulares</span><span class="sxs-lookup"><span data-stu-id="1d4c1-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="1d4c1-123">Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo*, ou uma referência circular, entre duas ou mais constantes.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="1d4c1-124">Um ciclo ocorre quando você tem duas ou mais constantes públicas, cada um deles é definida em termos de outro, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1d4c1-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="1d4c1-125">Se ocorrer um ciclo, o Visual Basic gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="1d4c1-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d4c1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d4c1-126">See also</span></span>
- [<span data-ttu-id="1d4c1-127">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="1d4c1-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="1d4c1-128">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="1d4c1-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="1d4c1-129">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="1d4c1-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="1d4c1-130">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="1d4c1-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="1d4c1-131">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="1d4c1-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="1d4c1-132">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="1d4c1-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="1d4c1-133">Como: Declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="1d4c1-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="1d4c1-134">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="1d4c1-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="1d4c1-135">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="1d4c1-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
