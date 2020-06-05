---
title: Instrução Get
ms.date: 07/20/2015
f1_keywords:
- vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
ms.openlocfilehash: 31936fb2c8f658203a43702a2b5fa4ee2481beb5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404596"
---
# <a name="get-statement"></a><span data-ttu-id="59d83-102">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="59d83-102">Get Statement</span></span>
<span data-ttu-id="59d83-103">Declara um `Get` procedimento de propriedade usado para recuperar o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59d83-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59d83-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="59d83-105">Partes</span><span class="sxs-lookup"><span data-stu-id="59d83-105">Parts</span></span>  
  
|<span data-ttu-id="59d83-106">Termo</span><span class="sxs-lookup"><span data-stu-id="59d83-106">Term</span></span>|<span data-ttu-id="59d83-107">Definição</span><span class="sxs-lookup"><span data-stu-id="59d83-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="59d83-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-108">Optional.</span></span> <span data-ttu-id="59d83-109">Consulte a [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="59d83-109">See [Attribute List](attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="59d83-110">Opcional em no máximo uma das `Get` instruções e `Set` nesta propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="59d83-111">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="59d83-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="59d83-112">-   [Protected](../modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="59d83-112">-   [Protected](../modifiers/protected.md)</span></span><br /><span data-ttu-id="59d83-113">-   [Público](../modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="59d83-113">-   [Friend](../modifiers/friend.md)</span></span><br /><span data-ttu-id="59d83-114">-   [Pessoal](../modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="59d83-114">-   [Private](../modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="59d83-115">Consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="59d83-115">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="59d83-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="59d83-116">Optional.</span></span> <span data-ttu-id="59d83-117">Uma ou mais instruções que são executadas quando o `Get` procedimento de propriedade é chamado.</span><span class="sxs-lookup"><span data-stu-id="59d83-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="59d83-118">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="59d83-118">Required.</span></span> <span data-ttu-id="59d83-119">Encerra a definição do procedimento de `Get` propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59d83-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="59d83-120">Remarks</span></span>  
 <span data-ttu-id="59d83-121">Cada propriedade deve ter um `Get` procedimento de propriedade, a menos que a propriedade esteja marcada `WriteOnly` .</span><span class="sxs-lookup"><span data-stu-id="59d83-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="59d83-122">O `Get` procedimento é usado para retornar o valor atual da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="59d83-123">Visual Basic chama automaticamente o procedimento de uma propriedade `Get` quando uma expressão solicita o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="59d83-124">O corpo da declaração de propriedade pode conter somente as propriedades `Get` e os `Set` procedimentos entre a [instrução de propriedade](property-statement.md) e a `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="59d83-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="59d83-125">Ele não pode armazenar nada além desses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="59d83-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="59d83-126">Em particular, ele não pode armazenar o valor atual da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="59d83-127">Você deve armazenar esse valor fora da propriedade, porque se armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não poderá acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="59d83-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="59d83-128">A abordagem usual é armazenar o valor em uma variável [privada](../modifiers/private.md) declarada no mesmo nível da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-128">The usual approach is to store the value in a [Private](../modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="59d83-129">Você deve definir um `Get` procedimento dentro da propriedade à qual ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="59d83-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="59d83-130">O `Get` procedimento assume como padrão o nível de acesso de sua propriedade contendo, a menos que você use `accessmodifier` na `Get` instrução.</span><span class="sxs-lookup"><span data-stu-id="59d83-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="59d83-131">Regras</span><span class="sxs-lookup"><span data-stu-id="59d83-131">Rules</span></span>  
  
- <span data-ttu-id="59d83-132">**Níveis de acesso misto.**</span><span class="sxs-lookup"><span data-stu-id="59d83-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="59d83-133">Se você estiver definindo uma propriedade de leitura/gravação, poderá opcionalmente especificar um nível de acesso diferente para o `Get` ou o `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="59d83-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="59d83-134">Se você fizer isso, o nível de acesso do procedimento deverá ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="59d83-135">Por exemplo, se a propriedade for declarada `Friend` , você poderá declarar o `Get` procedimento `Private` , mas não `Public` .</span><span class="sxs-lookup"><span data-stu-id="59d83-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="59d83-136">Se você estiver definindo uma `ReadOnly` propriedade, o `Get` procedimento representará a propriedade inteira.</span><span class="sxs-lookup"><span data-stu-id="59d83-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="59d83-137">Não é possível declarar um nível de acesso diferente para `Get` , pois isso definiria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
- <span data-ttu-id="59d83-138">**Tipo de retorno.**</span><span class="sxs-lookup"><span data-stu-id="59d83-138">**Return Type.**</span></span> <span data-ttu-id="59d83-139">A [instrução Property](property-statement.md) pode declarar o tipo de dados do valor que ele retorna.</span><span class="sxs-lookup"><span data-stu-id="59d83-139">The [Property Statement](property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="59d83-140">O `Get` procedimento retorna automaticamente esse tipo de dados.</span><span class="sxs-lookup"><span data-stu-id="59d83-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="59d83-141">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, estrutura, classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="59d83-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="59d83-142">Se a `Property` instrução não especificar `returntype` , o procedimento retornará `Object` .</span><span class="sxs-lookup"><span data-stu-id="59d83-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="59d83-143">Comportamento</span><span class="sxs-lookup"><span data-stu-id="59d83-143">Behavior</span></span>  
  
- <span data-ttu-id="59d83-144">**Retornando de um procedimento.**</span><span class="sxs-lookup"><span data-stu-id="59d83-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="59d83-145">Quando o `Get` procedimento retorna ao código de chamada, a execução continua dentro da instrução que solicitou o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="59d83-146">`Get`os procedimentos de propriedade podem retornar um valor usando a [instrução return](return-statement.md) ou atribuindo o valor de retorno ao nome da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-146">`Get` property procedures can return a value using either the [Return Statement](return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="59d83-147">Para obter mais informações, consulte "valor de retorno" na [instrução function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="59d83-147">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="59d83-148">As `Exit Property` `Return` instruções e causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="59d83-149">Qualquer número de `Exit Property` `Return` instruções and pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` demonstrativos.</span><span class="sxs-lookup"><span data-stu-id="59d83-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
- <span data-ttu-id="59d83-150">**Valor de retorno.**</span><span class="sxs-lookup"><span data-stu-id="59d83-150">**Return Value.**</span></span> <span data-ttu-id="59d83-151">Para retornar um valor de um `Get` procedimento, você pode atribuir o valor ao nome da propriedade ou incluí-lo em uma [instrução return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="59d83-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](return-statement.md).</span></span> <span data-ttu-id="59d83-152">A `Return` instrução atribui simultaneamente o valor de `Get` retorno do procedimento e sai do procedimento.</span><span class="sxs-lookup"><span data-stu-id="59d83-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="59d83-153">Se você usar `Exit Property` sem atribuir um valor ao nome da propriedade, o `Get` procedimento retornará o valor padrão para o tipo de dados da propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="59d83-154">Para obter mais informações, consulte "valor de retorno" na [instrução function](function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="59d83-154">For more information, see "Return Value" in [Function Statement](function-statement.md).</span></span>  
  
     <span data-ttu-id="59d83-155">O exemplo a seguir ilustra duas maneiras como a propriedade somente leitura `quoteForTheDay` pode retornar o valor mantido na variável privada `quoteValue` .</span><span class="sxs-lookup"><span data-stu-id="59d83-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#27)]  
  
     [!code-vb[VbVbalrStatements#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#28)]  
  
     [!code-vb[VbVbalrStatements#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#29)]  
  
## <a name="example"></a><span data-ttu-id="59d83-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59d83-156">Example</span></span>  
 <span data-ttu-id="59d83-157">O exemplo a seguir usa a `Get` instrução para retornar o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="59d83-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="59d83-158">Confira também</span><span class="sxs-lookup"><span data-stu-id="59d83-158">See also</span></span>

- [<span data-ttu-id="59d83-159">Instrução SET</span><span class="sxs-lookup"><span data-stu-id="59d83-159">Set Statement</span></span>](set-statement.md)
- [<span data-ttu-id="59d83-160">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="59d83-160">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="59d83-161">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="59d83-161">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="59d83-162">Objetos e classes</span><span class="sxs-lookup"><span data-stu-id="59d83-162">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="59d83-163">Instruções passo a passo: definindo classes</span><span class="sxs-lookup"><span data-stu-id="59d83-163">Walkthrough: Defining Classes</span></span>](../../programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
