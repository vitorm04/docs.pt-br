---
title: Instrução Set (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
ms.openlocfilehash: dbc48d14bac54809e4ddd12c87429bf407169950
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604829"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="4d06f-102">Instrução Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d06f-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="4d06f-103">Declara uma `Set` procedimento de propriedade usado para atribuir um valor a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d06f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d06f-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="4d06f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4d06f-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="4d06f-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4d06f-106">Optional.</span></span> <span data-ttu-id="4d06f-107">Consulte [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4d06f-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="4d06f-108">Opcional no máximo uma da `Get` e `Set` instruções nesta propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="4d06f-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4d06f-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="4d06f-110">Protegido</span><span class="sxs-lookup"><span data-stu-id="4d06f-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="4d06f-111">Friend</span><span class="sxs-lookup"><span data-stu-id="4d06f-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="4d06f-112">Privado</span><span class="sxs-lookup"><span data-stu-id="4d06f-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="4d06f-113">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4d06f-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="4d06f-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4d06f-114">Required.</span></span> <span data-ttu-id="4d06f-115">Parâmetro que contém o novo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="4d06f-116">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="4d06f-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="4d06f-117">Tipo de dados a `value` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="4d06f-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="4d06f-118">O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade onde isso `Set` instrução é declarada.</span><span class="sxs-lookup"><span data-stu-id="4d06f-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="4d06f-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4d06f-119">Optional.</span></span> <span data-ttu-id="4d06f-120">Uma ou mais instruções que são executados quando o `Set` é chamado de procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="4d06f-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4d06f-121">Required.</span></span> <span data-ttu-id="4d06f-122">Finaliza a definição do `Set` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d06f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d06f-123">Remarks</span></span>  
 <span data-ttu-id="4d06f-124">Cada propriedade deve ter uma `Set` procedimento de propriedade, a menos que a propriedade é marcada como `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="4d06f-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="4d06f-125">O `Set` procedimento é usado para definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="4d06f-126">Visual Basic chama automaticamente uma propriedade `Set` procedimento quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="4d06f-127">Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="4d06f-128">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito denominada `value`.</span><span class="sxs-lookup"><span data-stu-id="4d06f-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="4d06f-129">O parâmetro armazena o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="4d06f-130">Você normalmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="4d06f-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="4d06f-131">O corpo da declaração de propriedade pode conter apenas da propriedade `Get` e `Set` procedimentos entre o [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="4d06f-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="4d06f-132">Não é possível armazenar nada além desses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="4d06f-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="4d06f-133">Em particular, não é possível armazenar o valor da propriedade atual.</span><span class="sxs-lookup"><span data-stu-id="4d06f-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="4d06f-134">Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo em qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não é possível acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="4d06f-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="4d06f-135">A abordagem comum é para armazenar o valor em uma [privada](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível como a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="4d06f-136">Você deve definir um `Set` procedimento dentro da propriedade à qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="4d06f-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="4d06f-137">O `Set` procedimento padrão é o nível de acesso da propriedade que o contém, a menos que você use `accessmodifier` no `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="4d06f-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4d06f-138">Regras</span><span class="sxs-lookup"><span data-stu-id="4d06f-138">Rules</span></span>  
  
-   <span data-ttu-id="4d06f-139">**Níveis de acesso mistos.**</span><span class="sxs-lookup"><span data-stu-id="4d06f-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="4d06f-140">Se você estiver definindo uma propriedade de leitura / gravação, você pode especificar opcionalmente um nível de acesso diferentes para cada uma a `Get` ou `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="4d06f-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="4d06f-141">Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="4d06f-142">Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="4d06f-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="4d06f-143">Se você estiver definindo um `WriteOnly` propriedade, o `Set` procedimento representa a propriedade de inteira.</span><span class="sxs-lookup"><span data-stu-id="4d06f-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="4d06f-144">Você não pode declarar um acesso a diferentes níveis de `Set`, pois isso configuraria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="4d06f-145">Comportamento</span><span class="sxs-lookup"><span data-stu-id="4d06f-145">Behavior</span></span>  
  
-   <span data-ttu-id="4d06f-146">**Retornando a partir de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="4d06f-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="4d06f-147">Quando o `Set` procedimento retorna para o código de chamada, a execução continua seguindo a declaração que forneceu o valor a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="4d06f-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="4d06f-148">`Set` procedimentos de propriedade podem retornar usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4d06f-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="4d06f-149">O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="4d06f-150">Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="4d06f-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d06f-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4d06f-151">Example</span></span>  
 <span data-ttu-id="4d06f-152">O exemplo a seguir usa o `Set` para definir o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="4d06f-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4d06f-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d06f-153">See Also</span></span>  
 [<span data-ttu-id="4d06f-154">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="4d06f-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="4d06f-155">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="4d06f-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="4d06f-156">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="4d06f-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="4d06f-157">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="4d06f-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
