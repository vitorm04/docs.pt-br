---
title: Sombras
ms.date: 07/20/2015
f1_keywords:
- vb.Shadows
- shadows
helpviewer_keywords:
- shadowing
- duplicate names [Visual Basic]
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic]
- names [Visual Basic], shadowing
ms.assetid: 6bf687cd-0544-4797-b51b-911125ec57c6
ms.openlocfilehash: 7aed6bec21bd484cca019b061bd5915de13a9eb8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402701"
---
# <a name="shadows-visual-basic"></a><span data-ttu-id="e1656-102">Sombras (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e1656-102">Shadows (Visual Basic)</span></span>

<span data-ttu-id="e1656-103">Especifica que um elemento de programação declarado redeclara e oculta um elemento de nome idêntico ou conjunto de elementos sobrecarregados, em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="e1656-103">Specifies that a declared programming element redeclares and hides an identically named element, or set of overloaded elements, in a base class.</span></span>

## <a name="remarks"></a><span data-ttu-id="e1656-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1656-104">Remarks</span></span>

<span data-ttu-id="e1656-105">A principal finalidade do sombreamento (que também é conhecido como *ocultar por nome*) é preservar a definição de seus membros de classe.</span><span class="sxs-lookup"><span data-stu-id="e1656-105">The main purpose of shadowing (which is also known as *hiding by name*) is to preserve the definition of your class members.</span></span> <span data-ttu-id="e1656-106">A classe base pode passar por uma alteração que cria um elemento com o mesmo nome de um que você já definiu.</span><span class="sxs-lookup"><span data-stu-id="e1656-106">The base class might undergo a change that creates an element with the same name as one you have already defined.</span></span> <span data-ttu-id="e1656-107">Se isso acontecer, o `Shadows` modificador força referências por meio de sua classe a ser resolvida para o membro que você definiu, em vez de para o novo elemento de classe base.</span><span class="sxs-lookup"><span data-stu-id="e1656-107">If this happens, the `Shadows` modifier forces references through your class to be resolved to the member you defined, instead of to the new base class element.</span></span>

<span data-ttu-id="e1656-108">Sombreamento e substituição redefinem um elemento herdado, mas há diferenças significativas entre as duas abordagens.</span><span class="sxs-lookup"><span data-stu-id="e1656-108">Both shadowing and overriding redefine an inherited element, but there are significant differences between the two approaches.</span></span> <span data-ttu-id="e1656-109">Para obter mais informações, consulte [sombreamento em Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span><span class="sxs-lookup"><span data-stu-id="e1656-109">For more information, see [Shadowing in Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).</span></span>

## <a name="rules"></a><span data-ttu-id="e1656-110">Regras</span><span class="sxs-lookup"><span data-stu-id="e1656-110">Rules</span></span>

- <span data-ttu-id="e1656-111">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="e1656-111">**Declaration Context.**</span></span> <span data-ttu-id="e1656-112">Você pode usar `Shadows` somente no nível de classe.</span><span class="sxs-lookup"><span data-stu-id="e1656-112">You can use `Shadows` only at class level.</span></span> <span data-ttu-id="e1656-113">Isso significa que o contexto de declaração para um `Shadows` elemento deve ser uma classe e não pode ser um arquivo de origem, namespace, interface, módulo, estrutura ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="e1656-113">This means the declaration context for a `Shadows` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

  <span data-ttu-id="e1656-114">Você pode declarar apenas um elemento de sombreamento em uma única instrução de declaração.</span><span class="sxs-lookup"><span data-stu-id="e1656-114">You can declare only one shadowing element in a single declaration statement.</span></span>

- <span data-ttu-id="e1656-115">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="e1656-115">**Combined Modifiers.**</span></span> <span data-ttu-id="e1656-116">Você não pode especificar `Shadows` juntos com `Overloads` , `Overrides` ou `Static` na mesma declaração.</span><span class="sxs-lookup"><span data-stu-id="e1656-116">You cannot specify `Shadows` together with `Overloads`, `Overrides`, or `Static` in the same declaration.</span></span>

- <span data-ttu-id="e1656-117">**Tipos de elemento.**</span><span class="sxs-lookup"><span data-stu-id="e1656-117">**Element Types.**</span></span> <span data-ttu-id="e1656-118">Você pode sombrear qualquer tipo de elemento declarado com qualquer outro tipo.</span><span class="sxs-lookup"><span data-stu-id="e1656-118">You can shadow any kind of declared element with any other kind.</span></span> <span data-ttu-id="e1656-119">Se você sombrear uma propriedade ou um procedimento com outra propriedade ou procedimento, os parâmetros e o tipo de retorno não precisarão corresponder àqueles na propriedade ou procedimento da classe base.</span><span class="sxs-lookup"><span data-stu-id="e1656-119">If you shadow a property or procedure with another property or procedure, the parameters and the return type do not have to match those in the base class property or procedure.</span></span>

- <span data-ttu-id="e1656-120">**Acess.**</span><span class="sxs-lookup"><span data-stu-id="e1656-120">**Accessing.**</span></span> <span data-ttu-id="e1656-121">O elemento sombreado na classe base normalmente não está disponível de dentro da classe derivada que a sombreia.</span><span class="sxs-lookup"><span data-stu-id="e1656-121">The shadowed element in the base class is normally unavailable from within the derived class that shadows it.</span></span> <span data-ttu-id="e1656-122">No entanto, as considerações a seguir se aplicam.</span><span class="sxs-lookup"><span data-stu-id="e1656-122">However, the following considerations apply.</span></span>

  - <span data-ttu-id="e1656-123">Se o elemento de sombreamento não estiver acessível a partir do código que se refere a ele, a referência será resolvida para o elemento sombreado.</span><span class="sxs-lookup"><span data-stu-id="e1656-123">If the shadowing element is not accessible from the code referring to it, the reference is resolved to the shadowed element.</span></span> <span data-ttu-id="e1656-124">Por exemplo, se um `Private` elemento sombreia um elemento de classe base, o código que não tem permissão para acessar `Private` o elemento acessa o elemento de classe base em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e1656-124">For example, if a `Private` element shadows a base class element, code that does not have permission to access the `Private` element accesses the base class element instead.</span></span>

  - <span data-ttu-id="e1656-125">Se você sombrear um elemento, ainda poderá acessar o elemento sombreado por meio de um objeto declarado com o tipo da classe base.</span><span class="sxs-lookup"><span data-stu-id="e1656-125">If you shadow an element, you can still access the shadowed element through an object declared with the type of the base class.</span></span> <span data-ttu-id="e1656-126">Você também pode acessá-lo por meio do `MyBase` .</span><span class="sxs-lookup"><span data-stu-id="e1656-126">You can also access it through `MyBase`.</span></span>

<span data-ttu-id="e1656-127">O `Shadows` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="e1656-127">The `Shadows` modifier can be used in these contexts:</span></span>

- [<span data-ttu-id="e1656-128">Instrução Class</span><span class="sxs-lookup"><span data-stu-id="e1656-128">Class Statement</span></span>](../statements/class-statement.md)

- [<span data-ttu-id="e1656-129">Instrução Const</span><span class="sxs-lookup"><span data-stu-id="e1656-129">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="e1656-130">Instrução Declare</span><span class="sxs-lookup"><span data-stu-id="e1656-130">Declare Statement</span></span>](../statements/declare-statement.md)

- [<span data-ttu-id="e1656-131">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="e1656-131">Delegate Statement</span></span>](../statements/delegate-statement.md)

- [<span data-ttu-id="e1656-132">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="e1656-132">Dim Statement</span></span>](../statements/dim-statement.md)

- [<span data-ttu-id="e1656-133">Instrução Enum</span><span class="sxs-lookup"><span data-stu-id="e1656-133">Enum Statement</span></span>](../statements/enum-statement.md)

- [<span data-ttu-id="e1656-134">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="e1656-134">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="e1656-135">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="e1656-135">Function Statement</span></span>](../statements/function-statement.md)

- [<span data-ttu-id="e1656-136">Instrução Interface</span><span class="sxs-lookup"><span data-stu-id="e1656-136">Interface Statement</span></span>](../statements/interface-statement.md)

- [<span data-ttu-id="e1656-137">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="e1656-137">Property Statement</span></span>](../statements/property-statement.md)

- [<span data-ttu-id="e1656-138">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="e1656-138">Structure Statement</span></span>](../statements/structure-statement.md)

- [<span data-ttu-id="e1656-139">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="e1656-139">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="e1656-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="e1656-140">See also</span></span>

- [<span data-ttu-id="e1656-141">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="e1656-141">Shared</span></span>](shared.md)
- [<span data-ttu-id="e1656-142">Estático</span><span class="sxs-lookup"><span data-stu-id="e1656-142">Static</span></span>](static.md)
- [<span data-ttu-id="e1656-143">Privada</span><span class="sxs-lookup"><span data-stu-id="e1656-143">Private</span></span>](private.md)
- [<span data-ttu-id="e1656-144">Me, My, MyBase e MyClass</span><span class="sxs-lookup"><span data-stu-id="e1656-144">Me, My, MyBase, and MyClass</span></span>](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="e1656-145">Noções básicas de herança</span><span class="sxs-lookup"><span data-stu-id="e1656-145">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="e1656-146">MustOverride</span><span class="sxs-lookup"><span data-stu-id="e1656-146">MustOverride</span></span>](mustoverride.md)
- [<span data-ttu-id="e1656-147">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="e1656-147">NotOverridable</span></span>](notoverridable.md)
- [<span data-ttu-id="e1656-148">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="e1656-148">Overloads</span></span>](overloads.md)
- [<span data-ttu-id="e1656-149">Substituível</span><span class="sxs-lookup"><span data-stu-id="e1656-149">Overridable</span></span>](overridable.md)
- [<span data-ttu-id="e1656-150">Substituições</span><span class="sxs-lookup"><span data-stu-id="e1656-150">Overrides</span></span>](overrides.md)
- [<span data-ttu-id="e1656-151">Sombreamento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e1656-151">Shadowing in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/shadowing.md)
