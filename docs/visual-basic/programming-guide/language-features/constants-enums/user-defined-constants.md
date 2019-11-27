---
title: Constantes definidas pelo usuário
ms.date: 07/20/2015
helpviewer_keywords:
- constants [Visual Basic], circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants [Visual Basic]
- scope [Visual Basic], constants
- constants [Visual Basic], user-defined
- circular references between constants [Visual Basic]
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
ms.openlocfilehash: 194a420b3749ca5c858a65c07b8c164287c1582a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354013"
---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="e9ae5-102">Constantes definidas pelo usuário (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e9ae5-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="e9ae5-103">Uma constante é um nome significativo que substitui um número ou uma cadeia de caracteres que não é alterada.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="e9ae5-104">Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="e9ae5-105">Você pode usar constantes que são definidas pelos controles ou componentes com os quais você trabalha, ou você pode criar suas próprias.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="e9ae5-106">As constantes que você cria são descritas como *definidas pelo usuário*.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="e9ae5-107">Você declara uma constante com a instrução `Const`, usando as mesmas diretrizes para criar um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="e9ae5-108">Se `Option Strict` for `On`, você deverá declarar explicitamente o tipo de constante.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="e9ae5-109">Uso da instrução const</span><span class="sxs-lookup"><span data-stu-id="e9ae5-109">Const Statement Usage</span></span>  
 <span data-ttu-id="e9ae5-110">Uma instrução `Const` pode representar uma quantidade matemática ou de data/hora:</span><span class="sxs-lookup"><span data-stu-id="e9ae5-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 [!code-vb[VbEnumsTask#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#10)]  
  
 <span data-ttu-id="e9ae5-111">Ele também pode definir `String` constantes:</span><span class="sxs-lookup"><span data-stu-id="e9ae5-111">It also can define `String` constants:</span></span>  
  
 [!code-vb[VbEnumsTask#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#13)]  
  
 <span data-ttu-id="e9ae5-112">A expressão no lado direito do sinal de igual (`=`) geralmente é um número ou uma cadeia de caracteres literal, mas também pode ser uma expressão que resulte em um número ou cadeia de caracteres (embora essa expressão não possa conter chamadas para funções).</span><span class="sxs-lookup"><span data-stu-id="e9ae5-112">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="e9ae5-113">Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:</span><span class="sxs-lookup"><span data-stu-id="e9ae5-113">You can even define constants in terms of previously defined constants:</span></span>  
  
 [!code-vb[VbEnumsTask#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#15)]  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="e9ae5-114">Escopo de constantes definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e9ae5-114">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="e9ae5-115">O escopo de uma instrução de `Const` é o mesmo de uma variável declarada no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-115">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="e9ae5-116">Você pode especificar o escopo de qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="e9ae5-116">You can specify scope in any of the following ways:</span></span>  
  
- <span data-ttu-id="e9ae5-117">Para criar uma constante que existe somente dentro de um procedimento, declare-a dentro desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-117">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
- <span data-ttu-id="e9ae5-118">Para criar uma constante disponível para todos os procedimentos em uma classe, mas não para qualquer código fora desse módulo, declare-o na seção declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-118">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="e9ae5-119">Para criar uma constante que está disponível para todos os membros de um assembly, mas não para clientes externos do assembly, declare-o usando a palavra-chave `Friend` na seção declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-119">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
- <span data-ttu-id="e9ae5-120">Para criar uma constante disponível em todo o aplicativo, declare-a usando a palavra-chave `Public` na seção declarações a classe.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-120">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="e9ae5-121">Para obter mais informações, consulte [como: declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="e9ae5-121">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="e9ae5-122">Evitando referências circulares</span><span class="sxs-lookup"><span data-stu-id="e9ae5-122">Avoiding Circular References</span></span>  
 <span data-ttu-id="e9ae5-123">Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo*, ou referência circular, entre duas ou mais constantes.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-123">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="e9ae5-124">Um ciclo ocorre quando você tem duas ou mais constantes públicas, cada uma delas definida em termos do outro, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e9ae5-124">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 [!code-vb[VbEnumsTask#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#16)]  
[!code-vb[VbEnumsTask#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#17)]  
  
 <span data-ttu-id="e9ae5-125">Se ocorrer um ciclo, Visual Basic gerará um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="e9ae5-125">If a cycle occurs, Visual Basic generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ae5-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9ae5-126">See also</span></span>

- [<span data-ttu-id="e9ae5-127">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="e9ae5-127">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
- [<span data-ttu-id="e9ae5-128">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="e9ae5-128">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="e9ae5-129">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="e9ae5-129">Constants and Enumerations</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md)
- [<span data-ttu-id="e9ae5-130">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="e9ae5-130">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
- [<span data-ttu-id="e9ae5-131">Visão geral de Enumerações</span><span class="sxs-lookup"><span data-stu-id="e9ae5-131">Enumerations Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [<span data-ttu-id="e9ae5-132">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="e9ae5-132">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="e9ae5-133">Como declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="e9ae5-133">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [<span data-ttu-id="e9ae5-134">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="e9ae5-134">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="e9ae5-135">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="e9ae5-135">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
