---
title: 'Como: chamar um procedimento de propriedade (Visual Basic) | Documentos do Microsoft'
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
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
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
ms.openlocfilehash: d0d37fc2b7ae1d563a7e9d0a8e75343dd690089b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="658af-102">Como chamar um procedimento de propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="658af-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="658af-103">Você pode chamar um procedimento de propriedade ao armazenar um valor na propriedade ou recuperar seu valor.</span><span class="sxs-lookup"><span data-stu-id="658af-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="658af-104">Você acessa uma propriedade da mesma maneira que você acessa uma variável.</span><span class="sxs-lookup"><span data-stu-id="658af-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="658af-105">A propriedade `Set` procedimento armazena um valor e seu `Get` procedimento recupera o valor.</span><span class="sxs-lookup"><span data-stu-id="658af-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="658af-106">No entanto, você não explicitamente chamar esses procedimentos pelo nome.</span><span class="sxs-lookup"><span data-stu-id="658af-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="658af-107">Use a propriedade em uma instrução de atribuição ou uma expressão, exatamente como você poderia armazenar ou recuperar o valor de uma variável.</span><span class="sxs-lookup"><span data-stu-id="658af-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="658af-108">faz as chamadas aos procedimentos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="658af-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="658af-109">Para chamar procedimento Get uma propriedade do</span><span class="sxs-lookup"><span data-stu-id="658af-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="658af-110">Use o nome da propriedade em uma expressão da mesma maneira que você usaria um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="658af-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="658af-111">Você pode usar uma propriedade em qualquer lugar você pode usar uma variável ou uma constante.</span><span class="sxs-lookup"><span data-stu-id="658af-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="658af-112">-ou-</span><span class="sxs-lookup"><span data-stu-id="658af-112">-or-</span></span>  
  
     <span data-ttu-id="658af-113">Use o nome de propriedade seguido de igual (`=`) entrar em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="658af-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="658af-114">O exemplo a seguir lê o valor de <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>property, implicitamente chamando seu `Get` procedimento.</xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="658af-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="658af-115">[!code-vb[VbVbalrDateProperties n º&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="658af-115">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span></span>  
  
2.  <span data-ttu-id="658af-116">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="658af-116">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="658af-117">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="658af-117">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="658af-118">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="658af-118">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="658af-119">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="658af-119">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="658af-120">O valor da propriedade participa na expressão apenas como uma variável ou constante seria, ou ele é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="658af-120">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="658af-121">Para chamar uma propriedade do procedimento Set</span><span class="sxs-lookup"><span data-stu-id="658af-121">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="658af-122">Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="658af-122">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="658af-123">O exemplo a seguir define o valor de <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>property, implicitamente chamando o `Set` procedimento.</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span><span class="sxs-lookup"><span data-stu-id="658af-123">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     <span data-ttu-id="658af-124">[!code-vb[VbVbcnProcedures n º&11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="658af-124">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span></span>  
  
2.  <span data-ttu-id="658af-125">Se a propriedade utiliza argumentos, siga o nome da propriedade com parênteses para incluir a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="658af-125">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="658af-126">Se não houver nenhum argumento, opcionalmente, você pode omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="658af-126">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="658af-127">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="658af-127">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="658af-128">Certifique-se de que fornecer os argumentos na mesma ordem que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="658af-128">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="658af-129">O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="658af-129">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="658af-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="658af-130">See Also</span></span>  
 <span data-ttu-id="658af-131">[Procedimentos de propriedade](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="658af-131">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="658af-132"> [Argumentos e parâmetros de procedimento](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="658af-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="658af-133"> [Instrução Property](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="658af-133"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="658af-134"> [Diferenças entre propriedades e variáveis no Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="658af-134"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="658af-135"> [Como: criar uma propriedade](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="658af-135"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="658af-136"> [Como: declarar uma propriedade com níveis de acesso mistos](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="658af-136"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="658af-137"> [Como: declarar e chamar uma propriedade padrão no Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="658af-137"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="658af-138"> [Como: inserir um valor em uma propriedade](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="658af-138"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="658af-139"> [Como: obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="658af-139"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md) </span></span>  
<span data-ttu-id="658af-140"> [Instrução Get](../../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="658af-140"> [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="658af-141"> [Instrução Set](../../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="658af-141"> [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
