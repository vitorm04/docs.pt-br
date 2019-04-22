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
ms.openlocfilehash: 0a8d95ffbabf03a0e6c9d88edb28c248b60f3252
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839074"
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="04bef-102">Instrução Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04bef-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="04bef-103">Declara um `Set` procedimento de propriedade usado para atribuir um valor a uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04bef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04bef-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="04bef-105">Partes</span><span class="sxs-lookup"><span data-stu-id="04bef-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="04bef-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="04bef-106">Optional.</span></span> <span data-ttu-id="04bef-107">Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="04bef-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="04bef-108">Opcional no máximo um dos `Get` e `Set` as instruções nesta propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="04bef-109">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="04bef-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="04bef-110">Protegido</span><span class="sxs-lookup"><span data-stu-id="04bef-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="04bef-111">Friend</span><span class="sxs-lookup"><span data-stu-id="04bef-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="04bef-112">Privado</span><span class="sxs-lookup"><span data-stu-id="04bef-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="04bef-113">Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="04bef-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="04bef-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="04bef-114">Required.</span></span> <span data-ttu-id="04bef-115">Parâmetro que contém o novo valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="04bef-116">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="04bef-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="04bef-117">Tipo de dados do `value` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="04bef-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="04bef-118">O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade em que isso `Set` instrução é declarada.</span><span class="sxs-lookup"><span data-stu-id="04bef-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="04bef-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="04bef-119">Optional.</span></span> <span data-ttu-id="04bef-120">Uma ou mais instruções que são executados quando o `Set` procedimento de propriedade é chamado.</span><span class="sxs-lookup"><span data-stu-id="04bef-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="04bef-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="04bef-121">Required.</span></span> <span data-ttu-id="04bef-122">Finaliza a definição do `Set` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04bef-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="04bef-123">Remarks</span></span>  
 <span data-ttu-id="04bef-124">Cada propriedade deve ter uma `Set` procedimento de propriedade, a menos que a propriedade é marcada como `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="04bef-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="04bef-125">O `Set` procedimento é usado para definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="04bef-126">Visual Basic chama automaticamente uma propriedade `Set` procedimento quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="04bef-127">Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="04bef-128">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito chamada `value`.</span><span class="sxs-lookup"><span data-stu-id="04bef-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="04bef-129">O parâmetro contém o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="04bef-130">Você normalmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="04bef-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="04bef-131">O corpo da declaração de propriedade pode conter apenas da propriedade `Get` e `Set` procedimentos entre as [instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) e o `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="04bef-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="04bef-132">Não é possível armazenar qualquer coisa além desses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="04bef-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="04bef-133">Em particular, ele não é possível armazenar o valor da propriedade atual.</span><span class="sxs-lookup"><span data-stu-id="04bef-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="04bef-134">Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo dentro de qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não é possível acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="04bef-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="04bef-135">A abordagem comum é armazenar o valor em uma [privada](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível que a propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="04bef-136">Você deve definir um `Set` procedimento dentro da propriedade à qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="04bef-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="04bef-137">O `Set` procedimento assume como padrão o nível de acesso de sua propriedade contendo a menos que você use `accessmodifier` no `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="04bef-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="04bef-138">Regras</span><span class="sxs-lookup"><span data-stu-id="04bef-138">Rules</span></span>  
  
-   <span data-ttu-id="04bef-139">**Níveis de acesso mistos.**</span><span class="sxs-lookup"><span data-stu-id="04bef-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="04bef-140">Se você estiver definindo uma propriedade de leitura / gravação, você pode, opcionalmente, especificar um nível de acesso diferentes para qualquer um de `Get` ou o `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="04bef-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="04bef-141">Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="04bef-142">Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="04bef-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="04bef-143">Se você estiver definindo uma `WriteOnly` propriedade, o `Set` procedimento representa a propriedade de inteira.</span><span class="sxs-lookup"><span data-stu-id="04bef-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="04bef-144">Você não pode declarar um acesso a diferentes níveis para `Set`, pois isso configuraria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="04bef-145">Comportamento</span><span class="sxs-lookup"><span data-stu-id="04bef-145">Behavior</span></span>  
  
-   <span data-ttu-id="04bef-146">**Retornando de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="04bef-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="04bef-147">Quando o `Set` procedimento retorna para o código de chamada, a execução continua seguindo a declaração que forneceu o valor a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="04bef-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="04bef-148">`Set` procedimentos de propriedade podem retornar utilizando-se a [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou o [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="04bef-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="04bef-149">O `Exit Property` e `Return` instruções fazem com que uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="04bef-150">Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="04bef-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04bef-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04bef-151">Example</span></span>  
 <span data-ttu-id="04bef-152">O exemplo a seguir usa o `Set` instrução para definir o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="04bef-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#55)]  
  
## <a name="see-also"></a><span data-ttu-id="04bef-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04bef-153">See also</span></span>

- [<span data-ttu-id="04bef-154">Instrução Get</span><span class="sxs-lookup"><span data-stu-id="04bef-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
- [<span data-ttu-id="04bef-155">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="04bef-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="04bef-156">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="04bef-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="04bef-157">Procedimentos de Propriedade</span><span class="sxs-lookup"><span data-stu-id="04bef-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
