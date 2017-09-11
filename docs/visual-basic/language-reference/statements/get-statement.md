---
title: "Instrução Get | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Get
dev_langs:
- VB
helpviewer_keywords:
- Get statement, syntax
- Get statement
- properties [Visual Basic], read-only
- read-only properties
- Get keyword
- property procedures, Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
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
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 34d4db7478928f114d3ce86cfd78fa1eea33996f
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="get-statement"></a><span data-ttu-id="d5745-102">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="d5745-102">Get Statement</span></span>
<span data-ttu-id="d5745-103">Declara um `Get` usado para recuperar o valor de uma propriedade do procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5745-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5745-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="d5745-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d5745-105">Parts</span></span>  
  
|<span data-ttu-id="d5745-106">Termo</span><span class="sxs-lookup"><span data-stu-id="d5745-106">Term</span></span>|<span data-ttu-id="d5745-107">Definição</span><span class="sxs-lookup"><span data-stu-id="d5745-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="d5745-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d5745-108">Optional.</span></span> <span data-ttu-id="d5745-109">Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="d5745-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="d5745-110">Opcional, no máximo uma do `Get` e `Set` instruções nessa propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="d5745-111">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="d5745-111">Can be one of the following:</span></span><br /><br /><span data-ttu-id="d5745-112"> -   [Protegido](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="d5745-112"> -   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="d5745-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="d5745-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="d5745-114">-   [Privado](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="d5745-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="d5745-115">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d5745-115">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="d5745-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d5745-116">Optional.</span></span> <span data-ttu-id="d5745-117">Uma ou mais declarações que executam quando o `Get` procedimento de propriedade é chamado.</span><span class="sxs-lookup"><span data-stu-id="d5745-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="d5745-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="d5745-118">Required.</span></span> <span data-ttu-id="d5745-119">Finaliza a definição de `Get` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5745-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5745-120">Remarks</span></span>  
 <span data-ttu-id="d5745-121">Cada propriedade deve ter uma `Get` procedimento de propriedade, a menos que a propriedade é marcada como `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="d5745-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="d5745-122">O `Get` procedimento é usado para retornar o valor atual da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="d5745-123">Visual Basic chama automaticamente uma propriedade `Get` procedimento quando uma expressão solicita o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="d5745-124">O corpo da declaração de propriedade pode conter somente da propriedade `Get` e `Set` procedimentos entre o [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="d5745-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="d5745-125">Não é possível armazenar nada além desses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="d5745-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="d5745-126">Em particular, não é possível armazenar o valor da propriedade atual.</span><span class="sxs-lookup"><span data-stu-id="d5745-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="d5745-127">Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo em qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não pode acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="d5745-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="d5745-128">A abordagem usual é armazenar o valor em uma [particular](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="d5745-129">Você deve definir uma `Get` procedimento dentro da propriedade à qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="d5745-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="d5745-130">O `Get` procedimento assume como padrão o nível de acesso da propriedade que contém a menos que você use `accessmodifier` no `Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="d5745-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="d5745-131">Regras</span><span class="sxs-lookup"><span data-stu-id="d5745-131">Rules</span></span>  
  
-   <span data-ttu-id="d5745-132">**Níveis de acesso mistos.**</span><span class="sxs-lookup"><span data-stu-id="d5745-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="d5745-133">Se você estiver definindo uma propriedade de leitura / gravação, você pode opcionalmente especificar um nível de acesso diferente para o `Get` ou `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="d5745-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="d5745-134">Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="d5745-135">Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Get` procedimento `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="d5745-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="d5745-136">Se você estiver definindo um `ReadOnly` propriedade, o `Get` procedimento representa toda a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="d5745-137">Você não pode declarar um acesso a diferentes níveis de `Get`, pois isso configuraria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="d5745-138">**Tipo de retorno.**</span><span class="sxs-lookup"><span data-stu-id="d5745-138">**Return Type.**</span></span> <span data-ttu-id="d5745-139">O [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) pode declarar o tipo de dados do valor que ele retorna.</span><span class="sxs-lookup"><span data-stu-id="d5745-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="d5745-140">O `Get` procedimento retorna automaticamente esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="d5745-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="d5745-141">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="d5745-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="d5745-142">Se o `Property` não especifica a instrução `returntype`, o procedimento retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="d5745-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="d5745-143">Comportamento</span><span class="sxs-lookup"><span data-stu-id="d5745-143">Behavior</span></span>  
  
-   <span data-ttu-id="d5745-144">**Retornando a partir de um procedimento.**</span><span class="sxs-lookup"><span data-stu-id="d5745-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="d5745-145">Quando o `Get` procedimento retorna para o código de chamada, a execução continua dentro da declaração que solicitou o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="d5745-146">`Get`procedimentos de propriedade podem retornar um valor usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou atribuindo o valor de retorno ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="d5745-147">Para obter mais informações, consulte "Valor de retorno" em [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5745-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="d5745-148">O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="d5745-149">Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="d5745-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="d5745-150">**Valor de retorno.**</span><span class="sxs-lookup"><span data-stu-id="d5745-150">**Return Value.**</span></span> <span data-ttu-id="d5745-151">Para retornar um valor de uma `Get` procedimento, você pode atribuir o valor ao nome da propriedade ou incluí-lo em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5745-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="d5745-152">O `Return` instrução atribui simultaneamente o `Get` valor e finaliza o procedimento de retorno de procedimento.</span><span class="sxs-lookup"><span data-stu-id="d5745-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="d5745-153">Se você usar `Exit Property` sem atribuir um valor ao nome da propriedade, o `Get` procedimento retorna o valor padrão para o tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="d5745-154">Para obter mais informações, consulte "Valor de retorno" em [declaração de função](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5745-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="d5745-155">O exemplo a seguir ilustra duas maneiras a propriedade somente leitura `quoteForTheDay` pode retornar o valor retido na variável privada `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="d5745-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     <span data-ttu-id="d5745-156">[!code-vb[VbVbalrStatements&#27;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d5745-156">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="d5745-157">[!code-vb[VbVbalrStatements&#28;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="d5745-157">[!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]</span></span>  
  
     <span data-ttu-id="d5745-158">[!code-vb[29 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="d5745-158">[!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5745-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d5745-159">Example</span></span>  
 <span data-ttu-id="d5745-160">O exemplo a seguir usa o `Get` instrução para retornar o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="d5745-160">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 <span data-ttu-id="d5745-161">[!code-vb[30 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="d5745-161">[!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5745-162">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5745-162">See Also</span></span>  
 <span data-ttu-id="d5745-163">[Instrução Set](../../../visual-basic/language-reference/statements/set-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d5745-163">[Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) </span></span>  
<span data-ttu-id="d5745-164"> [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d5745-164"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="d5745-165"> [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="d5745-165"> [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md) </span></span>  
<span data-ttu-id="d5745-166"> [Objetos e Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="d5745-166"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="d5745-167"> [Instruções passo a passo: definindo classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span><span class="sxs-lookup"><span data-stu-id="d5745-167"> [Walkthrough: Defining Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)</span></span>

