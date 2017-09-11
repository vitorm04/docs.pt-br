---
title: "Visão geral de constantes (Visual Basic) | Documentos do Microsoft"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
ms.openlocfilehash: 2df21b9e3e814c654b355472aa645481060c6f68
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="e3fe3-102">Visão geral de constantes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3fe3-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="e3fe3-103">Uma constante é um nome significativo que toma o lugar de um número ou cadeia de caracteres que não são alterados.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="e3fe3-104">Constantes armazenam valores que, como o nome já diz, permanecem os mesmos durante a execução de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="e3fe3-105">Você pode significativamente melhorar a legibilidade do código e facilitar a manutenção usando constantes.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="e3fe3-106">Usá-los no código que contém valores que reaparecem ou dependem de certos números que são difíceis de lembrar ou não tem significado óbvio.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="e3fe3-107">Como criar e usar constantes</span><span class="sxs-lookup"><span data-stu-id="e3fe3-107">How to Create and Use Constants</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="e3fe3-108">contém um número de constantes pré-definidas, usadas principalmente para impressão e exibição.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-108"> contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="e3fe3-109">Você também pode criar suas próprias constantes com a `Const` declaração, usando as mesmas diretrizes que você faria para criar um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="e3fe3-110">Se `Option Strict` é `On`, você deve declarar explicitamente o tipo de constante.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="e3fe3-111">Escopo de uma constante, que é o conjunto de todo o código que pode fazer referência a ele sem qualificar seu nome, é o mesmo que uma variável declarada no mesmo local.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="e3fe3-112">Para criar uma constante que existe dentro do escopo de um determinado procedimento, declare-a dentro do procedimento.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="e3fe3-113">Para criar uma constante que está disponível em toda o aplicativo, declare-a usando o `Public` palavra-chave na seção de declarações da classe.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3fe3-114">Embora constantes de alguma maneira se assemelharem a variáveis, você não pode modificá-las ou atribuir novos valores para eles em variáveis.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="e3fe3-115">As constantes que você usa em seu código podem ser definidas pelo modelo de objeto para controles ou componentes que você trabalha com, ou podem ser definidos pelo usuário (ou seja, aqueles você mesmo cria).</span><span class="sxs-lookup"><span data-stu-id="e3fe3-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="e3fe3-116">Constantes de tempo de compilação e tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e3fe3-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="e3fe3-117">Uma constante de tempo de compilação é computada no momento em que o código é compilado, enquanto uma constante de tempo de execução pode ser calculada apenas enquanto o aplicativo é executado.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="e3fe3-118">Uma constante de tempo de compilação terá o mesmo valor cada vez que um aplicativo é executado, enquanto uma constante de tempo de execução pode mudar cada vez.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="e3fe3-119">Constantes de tempo de compilação são necessárias em casos como limites de matriz, expressões case ou inicializadores.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e3fe3-120">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e3fe3-120">In This Section</span></span>  
  
|<span data-ttu-id="e3fe3-121">Definição</span><span class="sxs-lookup"><span data-stu-id="e3fe3-121">Definition</span></span>|<span data-ttu-id="e3fe3-122">Termo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="e3fe3-123">Como declarar uma constante</span><span class="sxs-lookup"><span data-stu-id="e3fe3-123">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|<span data-ttu-id="e3fe3-124">Explica como usar o `Const` instrução para declarar uma constante e definir seu valor; ao declarar uma constante, você atribuir um nome significativo para o valor.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="e3fe3-125">Constantes Definidas pelo Usuário</span><span class="sxs-lookup"><span data-stu-id="e3fe3-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|<span data-ttu-id="e3fe3-126">Descreve como criar suas próprias constantes, incluindo informações sobre o escopo e como evitar referências circulares.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="e3fe3-127">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="e3fe3-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|<span data-ttu-id="e3fe3-128">Fornece informações sobre como o [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilador inicializa constantes quando `Option Explicit` está desativado.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-128">Provides information on how the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="e3fe3-129">Como agrupar valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="e3fe3-129">How to: Group Related Constant Values Together</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|<span data-ttu-id="e3fe3-130">Demonstra como agrupar valores constantes que estão relacionados.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="e3fe3-131">Referência</span><span class="sxs-lookup"><span data-stu-id="e3fe3-131">Reference</span></span>  
  
|<span data-ttu-id="e3fe3-132">Definição</span><span class="sxs-lookup"><span data-stu-id="e3fe3-132">Definition</span></span>|<span data-ttu-id="e3fe3-133">Termo</span><span class="sxs-lookup"><span data-stu-id="e3fe3-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="e3fe3-134">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="e3fe3-134">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|<span data-ttu-id="e3fe3-135">Lista as constantes predefinidas pelo [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="e3fe3-135">Lists the constants predefined by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>|  
|[<span data-ttu-id="e3fe3-136">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="e3fe3-136">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="e3fe3-137">Descreve o `Const` instrução e seu uso.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="e3fe3-138">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="e3fe3-138">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="e3fe3-139">Descreve o `Option Strict` instrução e seu uso.</span><span class="sxs-lookup"><span data-stu-id="e3fe3-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e3fe3-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3fe3-140">See Also</span></span>  
 <span data-ttu-id="e3fe3-141">[Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e3fe3-141">[Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="e3fe3-142"> [Como: inicializar uma variável de matriz no Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="e3fe3-142"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
