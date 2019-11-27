---
title: Como chamar um procedimento de propriedade
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
ms.openlocfilehash: 52e6c62ffb81c480ccc1abf06f04eb780218dbf1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340548"
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="725e5-102">Como chamar um procedimento de propriedade (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="725e5-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="725e5-103">Você chama um procedimento de propriedade armazenando um valor na propriedade ou recuperando seu valor.</span><span class="sxs-lookup"><span data-stu-id="725e5-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="725e5-104">Você acessa uma propriedade da mesma maneira que acessa uma variável.</span><span class="sxs-lookup"><span data-stu-id="725e5-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="725e5-105">O procedimento de `Set` da propriedade armazena um valor e seu procedimento de `Get` recupera o valor.</span><span class="sxs-lookup"><span data-stu-id="725e5-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="725e5-106">No entanto, você não chama explicitamente esses procedimentos por nome.</span><span class="sxs-lookup"><span data-stu-id="725e5-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="725e5-107">Você usa a propriedade em uma instrução de atribuição ou uma expressão, assim como você armazenaria ou recuperaria o valor de uma variável.</span><span class="sxs-lookup"><span data-stu-id="725e5-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> <span data-ttu-id="725e5-108">Visual Basic faz as chamadas para os procedimentos da propriedade.</span><span class="sxs-lookup"><span data-stu-id="725e5-108">Visual Basic makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="725e5-109">Para chamar o procedimento Get de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="725e5-109">To call a property's Get procedure</span></span>  
  
1. <span data-ttu-id="725e5-110">Use o nome da propriedade em uma expressão da mesma maneira que usaria um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="725e5-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="725e5-111">Você pode usar uma propriedade em qualquer lugar em que possa usar uma variável ou uma constante.</span><span class="sxs-lookup"><span data-stu-id="725e5-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="725e5-112">- ou -</span><span class="sxs-lookup"><span data-stu-id="725e5-112">-or-</span></span>  
  
     <span data-ttu-id="725e5-113">Use o nome da propriedade após o sinal de igual (`=`) em uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="725e5-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="725e5-114">O exemplo a seguir lê o valor da propriedade <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>, chamando implicitamente seu procedimento `Get`.</span><span class="sxs-lookup"><span data-stu-id="725e5-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDateProperties/VB/Module1.vb#4)]  
  
2. <span data-ttu-id="725e5-115">Se a propriedade usar argumentos, siga o nome da propriedade com parênteses para colocar a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="725e5-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="725e5-116">Se não houver argumentos, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="725e5-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="725e5-117">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="725e5-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="725e5-118">Certifique-se de fornecer os argumentos na mesma ordem em que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="725e5-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="725e5-119">O valor da propriedade participa da expressão, assim como uma variável ou constante, ou é armazenado na variável ou propriedade no lado esquerdo da instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="725e5-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="725e5-120">Para chamar o procedimento de conjunto de uma propriedade</span><span class="sxs-lookup"><span data-stu-id="725e5-120">To call a property's Set procedure</span></span>  
  
1. <span data-ttu-id="725e5-121">Use o nome da propriedade no lado esquerdo de uma instrução de atribuição.</span><span class="sxs-lookup"><span data-stu-id="725e5-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="725e5-122">O exemplo a seguir define o valor da propriedade <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>, chamando implicitamente o procedimento `Set`.</span><span class="sxs-lookup"><span data-stu-id="725e5-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#11)]  
  
2. <span data-ttu-id="725e5-123">Se a propriedade usar argumentos, siga o nome da propriedade com parênteses para colocar a lista de argumentos.</span><span class="sxs-lookup"><span data-stu-id="725e5-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="725e5-124">Se não houver argumentos, você pode opcionalmente omitir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="725e5-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3. <span data-ttu-id="725e5-125">Coloque os argumentos na lista de argumentos dentro dos parênteses, separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="725e5-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="725e5-126">Certifique-se de fornecer os argumentos na mesma ordem em que a propriedade define os parâmetros correspondentes.</span><span class="sxs-lookup"><span data-stu-id="725e5-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="725e5-127">O valor gerado no lado direito da instrução de atribuição é armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="725e5-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="725e5-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="725e5-128">See also</span></span>

- [<span data-ttu-id="725e5-129">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="725e5-129">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="725e5-130">Parâmetros e Argumentos de Procedimento</span><span class="sxs-lookup"><span data-stu-id="725e5-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="725e5-131">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="725e5-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="725e5-132">Diferenças entre propriedades e variáveis no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="725e5-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)
- [<span data-ttu-id="725e5-133">Como criar uma propriedade</span><span class="sxs-lookup"><span data-stu-id="725e5-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)
- [<span data-ttu-id="725e5-134">Como declarar uma propriedade com níveis de acesso mistos</span><span class="sxs-lookup"><span data-stu-id="725e5-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)
- [<span data-ttu-id="725e5-135">Como: declarar e chamar uma propriedade padrão no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="725e5-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)
- [<span data-ttu-id="725e5-136">Como inserir um valor em uma propriedade</span><span class="sxs-lookup"><span data-stu-id="725e5-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
- <span data-ttu-id="725e5-137">Como obter um valor de uma propriedade (Visual Basic)[Como obter um valor de uma propriedade](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="725e5-137">[How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
- [<span data-ttu-id="725e5-138">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="725e5-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="725e5-139">Instrução Set</span><span class="sxs-lookup"><span data-stu-id="725e5-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
