---
title: "Instrução Set (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Set
dev_langs:
- VB
helpviewer_keywords:
- property procedures, Set statements
- Set statement
- Set statement, syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
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
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 9284a9c8ffffba5eb5bb349d377d95d706e156f5
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="2cc01-102">Instrução Set (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cc01-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="2cc01-103">Declara um `Set` usado para atribuir um valor a uma propriedade do procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc01-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cc01-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="2cc01-105">Partes</span><span class="sxs-lookup"><span data-stu-id="2cc01-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="2cc01-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2cc01-106">Optional.</span></span> <span data-ttu-id="2cc01-107">Consulte [lista atributo](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="2cc01-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="2cc01-108">Opcional, no máximo uma do `Get` e `Set` instruções nessa propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="2cc01-109">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="2cc01-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="2cc01-110">Protegido</span><span class="sxs-lookup"><span data-stu-id="2cc01-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="2cc01-111">Friend</span><span class="sxs-lookup"><span data-stu-id="2cc01-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="2cc01-112">Privado</span><span class="sxs-lookup"><span data-stu-id="2cc01-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="2cc01-113">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2cc01-113">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="2cc01-114">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2cc01-114">Required.</span></span> <span data-ttu-id="2cc01-115">Parâmetro contendo o novo valor para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="2cc01-116">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="2cc01-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="2cc01-117">Tipo de dados a `value` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="2cc01-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="2cc01-118">O tipo de dados especificado deve ser o mesmo que o tipo de dados da propriedade onde isso `Set` instrução é declarada.</span><span class="sxs-lookup"><span data-stu-id="2cc01-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="2cc01-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="2cc01-119">Optional.</span></span> <span data-ttu-id="2cc01-120">Uma ou mais declarações que executam quando o `Set` procedimento de propriedade é chamado.</span><span class="sxs-lookup"><span data-stu-id="2cc01-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="2cc01-121">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2cc01-121">Required.</span></span> <span data-ttu-id="2cc01-122">Finaliza a definição de `Set` procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cc01-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="2cc01-123">Remarks</span></span>  
 <span data-ttu-id="2cc01-124">Cada propriedade deve ter uma `Set` procedimento de propriedade, a menos que a propriedade é marcada como `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="2cc01-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="2cc01-125">O `Set` procedimento é usado para definir o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="2cc01-126">Visual Basic chama automaticamente uma propriedade `Set` procedimento quando uma instrução de atribuição fornece um valor a ser armazenado na propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="2cc01-127">Visual Basic passa um parâmetro para o `Set` procedimento durante atribuições de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="2cc01-128">Se você não fornecer um parâmetro para `Set`, o ambiente de desenvolvimento integrado (IDE) usa uma parâmetro implícito chamada `value`.</span><span class="sxs-lookup"><span data-stu-id="2cc01-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="2cc01-129">O parâmetro armazena o valor a ser atribuído à propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="2cc01-130">Você geralmente armazena esse valor em uma variável local privada e retorná-lo sempre que o `Get` procedimento é chamado.</span><span class="sxs-lookup"><span data-stu-id="2cc01-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="2cc01-131">O corpo da declaração de propriedade pode conter somente da propriedade `Get` e `Set` procedimentos entre o [declaração de propriedade](../../../visual-basic/language-reference/statements/property-statement.md) e `End Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="2cc01-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="2cc01-132">Não é possível armazenar nada além desses procedimentos.</span><span class="sxs-lookup"><span data-stu-id="2cc01-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="2cc01-133">Em particular, não é possível armazenar o valor da propriedade atual.</span><span class="sxs-lookup"><span data-stu-id="2cc01-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="2cc01-134">Você deve armazenar esse valor fora da propriedade, porque se você armazená-lo em qualquer um dos procedimentos de propriedade, o outro procedimento de propriedade não pode acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="2cc01-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="2cc01-135">A abordagem usual é armazenar o valor em uma [particular](../../../visual-basic/language-reference/modifiers/private.md) variável declarada no mesmo nível da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="2cc01-136">Você deve definir uma `Set` procedimento dentro da propriedade à qual se aplica.</span><span class="sxs-lookup"><span data-stu-id="2cc01-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="2cc01-137">O `Set` procedimento assume como padrão o nível de acesso da propriedade que contém a menos que você use `accessmodifier` no `Set` instrução.</span><span class="sxs-lookup"><span data-stu-id="2cc01-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="2cc01-138">Regras</span><span class="sxs-lookup"><span data-stu-id="2cc01-138">Rules</span></span>  
  
-   <span data-ttu-id="2cc01-139">**Níveis de acesso mistos.**</span><span class="sxs-lookup"><span data-stu-id="2cc01-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="2cc01-140">Se você estiver definindo uma propriedade de leitura / gravação, você pode opcionalmente especificar um nível de acesso diferente para o `Get` ou `Set` procedimento, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="2cc01-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="2cc01-141">Se você fizer isso, o nível de acesso do procedimento deve ser mais restritivo do que o nível de acesso da propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="2cc01-142">Por exemplo, se a propriedade é declarada `Friend`, você pode declarar o `Set` procedimento `Private`, mas não `Public`.</span><span class="sxs-lookup"><span data-stu-id="2cc01-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="2cc01-143">Se você estiver definindo um `WriteOnly` propriedade, o `Set` procedimento representa toda a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="2cc01-144">Você não pode declarar um acesso a diferentes níveis de `Set`, pois isso configuraria dois níveis de acesso para a propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2cc01-145">Comportamento</span><span class="sxs-lookup"><span data-stu-id="2cc01-145">Behavior</span></span>  
  
-   <span data-ttu-id="2cc01-146">**Retornando a partir de um procedimento de propriedade.**</span><span class="sxs-lookup"><span data-stu-id="2cc01-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="2cc01-147">Quando o `Set` procedimento retorna para o código de chamada, a execução continua seguindo a declaração que forneceu o valor a ser armazenado.</span><span class="sxs-lookup"><span data-stu-id="2cc01-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="2cc01-148">`Set`procedimentos de propriedade podem retornar usando o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) ou [instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2cc01-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="2cc01-149">O `Exit Property` e `Return` instruções causam uma saída imediata de um procedimento de propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="2cc01-150">Qualquer número de `Exit Property` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Property` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="2cc01-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cc01-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2cc01-151">Example</span></span>  
 <span data-ttu-id="2cc01-152">O exemplo a seguir usa o `Set` para definir o valor de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="2cc01-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 <span data-ttu-id="2cc01-153">[!code-vb[VbVbalrStatements&#55;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2cc01-153">[!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cc01-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2cc01-154">See Also</span></span>  
 <span data-ttu-id="2cc01-155">[Instrução Get](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2cc01-155">[Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="2cc01-156"> [Instrução Property](../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2cc01-156"> [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="2cc01-157"> [Instrução sub](../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="2cc01-157"> [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="2cc01-158"> [Procedimentos de Propriedade](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)</span><span class="sxs-lookup"><span data-stu-id="2cc01-158"> [Property Procedures](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)</span></span>

