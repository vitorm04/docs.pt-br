---
title: Sobrecargas (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Overloads
- Overloads
helpviewer_keywords:
- Overloads keyword [Visual Basic]
- hiding by signature
- Shadows keyword [Visual Basic]
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
ms.openlocfilehash: ab8660ff0cf02956e760132f5aad69e359913950
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661092"
---
# <a name="overloads-visual-basic"></a><span data-ttu-id="220e0-102">Sobrecargas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="220e0-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="220e0-103">Especifica que uma propriedade ou procedimento redeclara uma ou mais propriedades ou procedimentos existentes com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="220e0-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="220e0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="220e0-104">Remarks</span></span>  
 <span data-ttu-id="220e0-105">*Sobrecarregando* é a prática de fornecer mais de uma definição para um determinado nome de propriedade ou procedimento no mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="220e0-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="220e0-106">Às vezes é chamado declarar uma propriedade ou procedimento com uma assinatura diferente *ocultação por assinatura*.</span><span class="sxs-lookup"><span data-stu-id="220e0-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="220e0-107">Regras</span><span class="sxs-lookup"><span data-stu-id="220e0-107">Rules</span></span>  
  
- <span data-ttu-id="220e0-108">**Contexto da declaração.**</span><span class="sxs-lookup"><span data-stu-id="220e0-108">**Declaration Context.**</span></span> <span data-ttu-id="220e0-109">Você pode usar `Overloads` somente em uma instrução de declaração de propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="220e0-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
- <span data-ttu-id="220e0-110">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="220e0-110">**Combined Modifiers.**</span></span> <span data-ttu-id="220e0-111">Não é possível especificar `Overloads` junto com [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) na mesma declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="220e0-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
- <span data-ttu-id="220e0-112">**Diferenças necessárias.**</span><span class="sxs-lookup"><span data-stu-id="220e0-112">**Required Differences.**</span></span> <span data-ttu-id="220e0-113">O *assinatura* nessa declaração deve ser diferente da assinatura de cada propriedade ou procedimento que ela sobrecarrega.</span><span class="sxs-lookup"><span data-stu-id="220e0-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="220e0-114">A assinatura inclui o nome de propriedade ou procedimento junto com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="220e0-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    - <span data-ttu-id="220e0-115">o número de parâmetros</span><span class="sxs-lookup"><span data-stu-id="220e0-115">the number of parameters</span></span>  
  
    - <span data-ttu-id="220e0-116">a ordem dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="220e0-116">the order of the parameters</span></span>  
  
    - <span data-ttu-id="220e0-117">os tipos de dados dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="220e0-117">the data types of the parameters</span></span>  
  
    - <span data-ttu-id="220e0-118">o número de parâmetros de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="220e0-118">the number of type parameters (for a generic procedure)</span></span>  
  
    - <span data-ttu-id="220e0-119">o tipo de retorno (somente para um procedimento de operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="220e0-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="220e0-120">Todas as sobrecargas devem ter o mesmo nome, mas cada um deve ser diferente de todas as outras em uma ou mais dentre as condições citadas.</span><span class="sxs-lookup"><span data-stu-id="220e0-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="220e0-121">Isso permite que o compilador a distinguir qual versão usar quando o código chama a propriedade ou procedimento.</span><span class="sxs-lookup"><span data-stu-id="220e0-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
- <span data-ttu-id="220e0-122">**Diferenças não permitidas.**</span><span class="sxs-lookup"><span data-stu-id="220e0-122">**Disallowed Differences.**</span></span> <span data-ttu-id="220e0-123">Alterar um ou mais dos procedimentos a seguir não é válido para a sobrecarga de uma propriedade ou procedimento, porque eles não fazem parte da assinatura:</span><span class="sxs-lookup"><span data-stu-id="220e0-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    - <span data-ttu-id="220e0-124">Se ele retorna um valor (para um procedimento)</span><span class="sxs-lookup"><span data-stu-id="220e0-124">whether or not it returns a value (for a procedure)</span></span>  
  
    - <span data-ttu-id="220e0-125">o tipo de dados do valor de retorno (exceto para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="220e0-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    - <span data-ttu-id="220e0-126">os nomes dos parâmetros ou parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="220e0-126">the names of the parameters or type parameters</span></span>  
  
    - <span data-ttu-id="220e0-127">as restrições as parâmetros de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="220e0-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    - <span data-ttu-id="220e0-128">palavras-chave de modificador de parâmetro (como `ByRef` ou `Optional`)</span><span class="sxs-lookup"><span data-stu-id="220e0-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    - <span data-ttu-id="220e0-129">propriedade ou procedimento palavras-chave de modificador (como `Public` ou `Shared`)</span><span class="sxs-lookup"><span data-stu-id="220e0-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
- <span data-ttu-id="220e0-130">**Modificador opcional.**</span><span class="sxs-lookup"><span data-stu-id="220e0-130">**Optional Modifier.**</span></span> <span data-ttu-id="220e0-131">Você não precisa usar o `Overloads` modificador quando você estiver definindo várias propriedades ou procedimentos sobrecarregados na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="220e0-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="220e0-132">No entanto, se você usar `Overloads` em uma das declarações, você deve usá-lo em todos eles.</span><span class="sxs-lookup"><span data-stu-id="220e0-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
- <span data-ttu-id="220e0-133">**Sombreamento e sobrecarga.**</span><span class="sxs-lookup"><span data-stu-id="220e0-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="220e0-134">`Overloads` também pode ser usado para sombrear um membro existente, ou conjunto de membros sobrecarregados, em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="220e0-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="220e0-135">Quando você usa `Overloads` dessa forma, você declara a propriedade ou método com o mesmo nome e a mesma lista de parâmetros como membro da classe base, e você não fornecer o `Shadows` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="220e0-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="220e0-136">Se você usar `Overrides`, o compilador adicionará implicitamente `Overloads` para que sua biblioteca de APIs de trabalhar com C# com mais facilidade.</span><span class="sxs-lookup"><span data-stu-id="220e0-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="220e0-137">O `Overloads` modificador pode ser usado nestes contextos:</span><span class="sxs-lookup"><span data-stu-id="220e0-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="220e0-138">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="220e0-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="220e0-139">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="220e0-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="220e0-140">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="220e0-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="220e0-141">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="220e0-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="220e0-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="220e0-142">See also</span></span>

- [<span data-ttu-id="220e0-143">Sombras</span><span class="sxs-lookup"><span data-stu-id="220e0-143">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="220e0-144">Sobrecarga de Procedimento</span><span class="sxs-lookup"><span data-stu-id="220e0-144">Procedure Overloading</span></span>](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md)
- [<span data-ttu-id="220e0-145">Tipos genéricos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="220e0-145">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="220e0-146">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="220e0-146">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="220e0-147">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="220e0-147">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
