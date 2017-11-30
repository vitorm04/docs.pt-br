---
title: Como chamar um procedimento de propriedade (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="e3c38-102">Como chamar um procedimento de propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3c38-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="e3c38-103">Para chamar um procedimento de propriedade, armazenar um valor na propriedade ou recuperar seu valor.</span><span class="sxs-lookup"><span data-stu-id="e3c38-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="e3c38-104">Você acessa uma propriedade da mesma maneira que você acessa uma variável.</span><span class="sxs-lookup"><span data-stu-id="e3c38-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="e3c38-105">A propriedade `Set` procedimento armazena um valor e seu `Get` procedimento recupera o valor.</span><span class="sxs-lookup"><span data-stu-id="e3c38-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="e3c38-106">No entanto, você não explicitamente chamar esses procedimentos por nome.</span><span class="sxs-lookup"><span data-stu-id="e3c38-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="e3c38-107">Você usar a propriedade em uma instrução de atribuição ou uma expressão, exatamente como você poderia armazenar ou recuperar o valor de uma variável.</span><span class="sxs-lookup"><span data-stu-id="e3c38-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e3c38-108">faz as chamadas aos procedimentos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3c38-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="e3c38-109">Para chamar um procedimento da propriedade Get</span><span class="sxs-lookup"><span data-stu-id="e3c38-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="e3c38-110">Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="e3c38-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="e3c38-111">Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou constante.</span><span class="sxs-lookup"><span data-stu-id="e3c38-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="e3c38-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="e3c38-112">-or-</span></span>  
  
     <span data-ttu-id="e3c38-113">Use o nome de propriedade seguido de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e3c38-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="e3c38-114">O exemplo a seguir lê o valor de <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitamente chamando seu `Get` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e3c38-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="e3c38-115">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="e3c38-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="e3c38-116">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="e3c38-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="e3c38-117">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="e3c38-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="e3c38-118">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e3c38-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="e3c38-119">O valor da propriedade participa na expressão apenas como uma variável ou constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e3c38-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="e3c38-120">Para chamar uma propriedade do procedimento Set</span><span class="sxs-lookup"><span data-stu-id="e3c38-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="e3c38-121">Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e3c38-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="e3c38-122">O exemplo a seguir define o valor de <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitamente chamando o `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="e3c38-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="e3c38-123">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="e3c38-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="e3c38-124">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="e3c38-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="e3c38-125">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="e3c38-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="e3c38-126">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e3c38-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="e3c38-127">O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="e3c38-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c38-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3c38-128">See Also</span></span>  
 [<span data-ttu-id="e3c38-129">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="e3c38-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="e3c38-130">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="e3c38-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="e3c38-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="e3c38-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="e3c38-132">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3c38-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="e3c38-133">Como criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="e3c38-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="e3c38-134">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="e3c38-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="e3c38-135">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3c38-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="e3c38-136">Como inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="e3c38-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 <span data-ttu-id="e3c38-137">Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="e3c38-137">[How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>  
 [<span data-ttu-id="e3c38-138">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="e3c38-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="e3c38-139">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="e3c38-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
