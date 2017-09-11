---
title: "Constantes (Visual Basic) definidos pelo usuário | Documentos do Microsoft"
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
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
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
ms.openlocfilehash: b1ab1501309823b1565d5198fff25edf2927a2ce
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="28cbc-102">Constantes definidas pelo usuário (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28cbc-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="28cbc-103">Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados.</span><span class="sxs-lookup"><span data-stu-id="28cbc-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="28cbc-104">Constantes armazenam valores que, como o nome implica, permanecem constantes durante a execução de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="28cbc-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="28cbc-105">Você pode usar constantes definidas por controles ou componentes que funcionam com ou você pode criar seus próprios.</span><span class="sxs-lookup"><span data-stu-id="28cbc-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="28cbc-106">Constantes que você mesmo cria são descritas como *definidos pelo usuário*.</span><span class="sxs-lookup"><span data-stu-id="28cbc-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="28cbc-107">Declarar uma constante com o `Const` instrução, usando as mesmas diretrizes que você faria para criar um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="28cbc-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="28cbc-108">Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.</span><span class="sxs-lookup"><span data-stu-id="28cbc-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="28cbc-109">Uso da instrução Const</span><span class="sxs-lookup"><span data-stu-id="28cbc-109">Const Statement Usage</span></span>  
 <span data-ttu-id="28cbc-110">Um `Const` declaração pode representar uma matemática ou quantidade de data/hora:</span><span class="sxs-lookup"><span data-stu-id="28cbc-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 <span data-ttu-id="28cbc-111">[!code-vb[VbEnumsTask n º&10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="28cbc-111">[!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span></span>  
  
 <span data-ttu-id="28cbc-112">Ele também pode definir `String` constantes:</span><span class="sxs-lookup"><span data-stu-id="28cbc-112">It also can define `String` constants:</span></span>  
  
 <span data-ttu-id="28cbc-113">[!code-vb[VbEnumsTask&13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="28cbc-113">[!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span></span>  
  
 <span data-ttu-id="28cbc-114">A expressão à direita do sinal de igual ( `=` ) é geralmente um número ou cadeia de caracteres literal, mas também pode ser uma expressão que resulta em um número ou cadeia de caracteres (embora essa expressão não pode conter chamadas a funções).</span><span class="sxs-lookup"><span data-stu-id="28cbc-114">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="28cbc-115">Você pode até mesmo definir constantes em termos de constantes definidas anteriormente:</span><span class="sxs-lookup"><span data-stu-id="28cbc-115">You can even define constants in terms of previously defined constants:</span></span>  
  
 <span data-ttu-id="28cbc-116">[!code-vb[VbEnumsTask&#15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="28cbc-116">[!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span></span>  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="28cbc-117">Escopo de constantes definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="28cbc-117">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="28cbc-118">Um `Const` escopo da instrução é o mesmo que uma variável declarada no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="28cbc-118">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="28cbc-119">Você pode especificar o escopo em qualquer uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="28cbc-119">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="28cbc-120">Para criar uma constante que existe somente dentro de um procedimento, declare-a dentro desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="28cbc-120">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="28cbc-121">Para criar uma constante disponível para todos os procedimentos dentro de uma classe, mas não para qualquer código fora desse módulo, declare-o na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="28cbc-121">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="28cbc-122">Para criar uma constante que está disponível para todos os membros de um assembly, mas não para clientes fora do assembly, declare-a usando o `Friend` palavra-chave na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="28cbc-122">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="28cbc-123">Para criar uma constante disponível em todo o aplicativo, declare-a usando o `Public` seção de palavra-chave nas declarações de classe.</span><span class="sxs-lookup"><span data-stu-id="28cbc-123">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="28cbc-124">Para obter mais informações, consulte [como: declarar uma constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="28cbc-124">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="28cbc-125">Evitando referências circulares</span><span class="sxs-lookup"><span data-stu-id="28cbc-125">Avoiding Circular References</span></span>  
 <span data-ttu-id="28cbc-126">Como constantes podem ser definidas em termos de outras constantes, é possível criar inadvertidamente um *ciclo*, ou referência circular, entre duas ou mais constantes.</span><span class="sxs-lookup"><span data-stu-id="28cbc-126">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="28cbc-127">Um ciclo ocorre quando você tiver duas ou mais constantes públicas, cada um deles é definida em termos da outra, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="28cbc-127">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 <span data-ttu-id="28cbc-128">[!code-vb[VbEnumsTask n º&16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="28cbc-128">[!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span></span>  
<span data-ttu-id="28cbc-129">[!code-vb[17 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="28cbc-129">[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span></span>  
  
 <span data-ttu-id="28cbc-130">Se ocorrer um ciclo, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gera um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="28cbc-130">If a cycle occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28cbc-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28cbc-131">See Also</span></span>  
 <span data-ttu-id="28cbc-132">[Instrução Const](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-132">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="28cbc-133"> [Tipos de dados constante e Literal](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-133"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="28cbc-134"> [Constantes e enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-134"> [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span></span>  
<span data-ttu-id="28cbc-135"> [Constantes e enumerações](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-135"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span></span>  
<span data-ttu-id="28cbc-136"> [Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-136"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="28cbc-137"> [Visão geral de constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-137"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="28cbc-138"> [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-138"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="28cbc-139"> [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="28cbc-139"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="28cbc-140"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="28cbc-140"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
