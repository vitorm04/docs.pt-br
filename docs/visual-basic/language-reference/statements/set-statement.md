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
ms.openlocfilehash: cb0dc76d110f3e6a3ea3e74cc0bfb5a669b35396
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583234"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="2ff9d-102">Instrução Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ff9d-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="2ff9d-103">Declara um procedimento de propriedade `Set` usado para atribuir um valor a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ff9d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ff9d-104">Syntax</span></span>  
  
```vb  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="2ff9d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2ff9d-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="2ff9d-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-106">Optional.</span></span> <span data-ttu-id="2ff9d-107">Consulte a [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="2ff9d-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="2ff9d-108">Opcional em no máximo uma das instruções `Get` e `Set` nesta propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="2ff9d-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="2ff9d-109">Can be one of the following:</span></span>  
  
- [<span data-ttu-id="2ff9d-110">Protegido</span><span class="sxs-lookup"><span data-stu-id="2ff9d-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
- [<span data-ttu-id="2ff9d-111">Friend</span><span class="sxs-lookup"><span data-stu-id="2ff9d-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
- [<span data-ttu-id="2ff9d-112">Privado</span><span class="sxs-lookup"><span data-stu-id="2ff9d-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
- `Protected Friend`  
  
 <span data-ttu-id="2ff9d-113">Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2ff9d-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="2ff9d-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-114">Required.</span></span> <span data-ttu-id="2ff9d-115">Parâmetro que contém o novo valor para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="2ff9d-116">Necessário se `Option Strict` for `On`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="2ff9d-117">Tipo de dados do parâmetro `value`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="2ff9d-118">O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade em que essa instrução `Set` é declarada.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="2ff9d-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-119">Optional.</span></span> <span data-ttu-id="2ff9d-120">Uma ou mais instruções que são executadas quando o procedimento de propriedade de `Set` é chamado.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="2ff9d-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-121">Required.</span></span> <span data-ttu-id="2ff9d-122">Encerra a definição do procedimento da propriedade `Set`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ff9d-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ff9d-123">Remarks</span></span>  
 <span data-ttu-id="2ff9d-124">Cada propriedade deve ter um procedimento de propriedade `Set`, a menos que a propriedade seja marcada `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="2ff9d-125">O procedimento `Set` é usado para definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="2ff9d-126">Visual Basic chama automaticamente o procedimento `Set` de uma propriedade quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="2ff9d-127">Visual Basic passa um parâmetro para o procedimento `Set` durante as atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="2ff9d-128">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usará um parâmetro implícito chamado `value`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="2ff9d-129">O parâmetro contém o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="2ff9d-130">Normalmente, você armazena esse valor em uma variável local privada e retorna-o sempre que o procedimento de `Get` é chamado.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="2ff9d-131">O corpo da declaração de propriedade pode conter apenas os procedimentos `Get` e `Set` da propriedade entre a [instrução de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e a instrução `End Property`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="2ff9d-132">Ele não pode armazenar nada além desses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="2ff9d-133">Em particular, ele não pode armazenar o valor atual da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="2ff9d-134">Você deve armazenar esse valor fora da propriedade, porque se armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não poderá acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="2ff9d-135">A abordagem usual é armazenar o valor em uma variável [privada](../../../visual-basic/language-reference/modifiers/private.md) declarada no mesmo nível da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="2ff9d-136">Você deve definir um procedimento `Set` dentro da propriedade à qual ele se aplica.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="2ff9d-137">O procedimento `Set` assume como padrão o nível de acesso de sua propriedade contendo, a menos que você use `accessmodifier` na instrução `Set`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2ff9d-138">Regras</span><span class="sxs-lookup"><span data-stu-id="2ff9d-138">Rules</span></span>  
  
- <span data-ttu-id="2ff9d-139">**Níveis de acesso misto.**</span><span class="sxs-lookup"><span data-stu-id="2ff9d-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="2ff9d-140">Se você estiver definindo uma propriedade de leitura/gravação, poderá opcionalmente especificar um nível de acesso diferente para o `Get` ou para o procedimento `Set`, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="2ff9d-141">Se você fizer isso, o nível de acesso do procedimento deverá ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="2ff9d-142">Por exemplo, se a propriedade for declarada `Friend`, você poderá declarar o procedimento `Set` `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="2ff9d-143">Se você estiver definindo uma propriedade `WriteOnly`, o procedimento `Set` representará a propriedade inteira.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="2ff9d-144">Você não pode declarar um nível de acesso diferente para `Set`, pois isso definiria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2ff9d-145">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2ff9d-145">Behavior</span></span>  
  
- <span data-ttu-id="2ff9d-146">**Retornando de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="2ff9d-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="2ff9d-147">Quando o procedimento de `Set` retorna ao código de chamada, a execução continua seguindo a instrução que forneceu o valor a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="2ff9d-148">`Set` procedimentos de propriedade podem ser retornados usando a [instrução return](../../../visual-basic/language-reference/statements/return-statement.md) ou a [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2ff9d-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="2ff9d-149">As instruções `Exit Property` e `Return` causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="2ff9d-150">Qualquer número de instruções `Exit Property` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e instruções `Return`.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ff9d-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2ff9d-151">Example</span></span>  
 <span data-ttu-id="2ff9d-152">O exemplo a seguir usa a instrução `Set` para definir o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="2ff9d-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="2ff9d-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ff9d-153">See also</span></span>

- [<span data-ttu-id="2ff9d-154">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="2ff9d-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="2ff9d-155">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="2ff9d-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2ff9d-156">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="2ff9d-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="2ff9d-157">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="2ff9d-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
