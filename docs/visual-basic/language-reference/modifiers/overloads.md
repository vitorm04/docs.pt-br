---
title: Sobrecargas (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Overloads
- Overloads
dev_langs:
- VB
helpviewer_keywords:
- Overloads keyword
- hiding by signature
- Shadows keyword
- signature, hiding by
ms.assetid: 0c6820b8-25b2-4664-bc59-5ca93c99c042
caps.latest.revision: 15
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
ms.openlocfilehash: 98e68e4f8b1c067a486bf6e1d70ae24275d608c8
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="overloads-visual-basic"></a><span data-ttu-id="df56c-102">Sobrecargas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="df56c-102">Overloads (Visual Basic)</span></span>
<span data-ttu-id="df56c-103">Especifica que uma propriedade ou procedimento declara novamente uma ou mais propriedades ou procedimentos existentes com o mesmo nome.</span><span class="sxs-lookup"><span data-stu-id="df56c-103">Specifies that a property or procedure redeclares one or more existing properties or procedures with the same name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df56c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="df56c-104">Remarks</span></span>  
 <span data-ttu-id="df56c-105">*Sobrecarga* é a prática de fornecer mais de uma definição para um determinado nome de propriedade ou procedimento no mesmo escopo.</span><span class="sxs-lookup"><span data-stu-id="df56c-105">*Overloading* is the practice of supplying more than one definition for a given property or procedure name in the same scope.</span></span> <span data-ttu-id="df56c-106">Declarar novamente um propriedade ou procedimento com uma assinatura diferente às vezes é chamado *ocultação por assinatura*.</span><span class="sxs-lookup"><span data-stu-id="df56c-106">Redeclaring a property or procedure with a different signature is sometimes called *hiding by signature*.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="df56c-107">Regras</span><span class="sxs-lookup"><span data-stu-id="df56c-107">Rules</span></span>  
  
-   <span data-ttu-id="df56c-108">**Contexto de declaração.**</span><span class="sxs-lookup"><span data-stu-id="df56c-108">**Declaration Context.**</span></span> <span data-ttu-id="df56c-109">Você pode usar `Overloads` somente na declaração de uma propriedade ou um procedimento.</span><span class="sxs-lookup"><span data-stu-id="df56c-109">You can use `Overloads` only in a property or procedure declaration statement.</span></span>  
  
-   <span data-ttu-id="df56c-110">**Modificadores combinados.**</span><span class="sxs-lookup"><span data-stu-id="df56c-110">**Combined Modifiers.**</span></span> <span data-ttu-id="df56c-111">Não é possível especificar `Overloads` junto com [sombras](../../../visual-basic/language-reference/modifiers/shadows.md) na mesma declaração de procedimento.</span><span class="sxs-lookup"><span data-stu-id="df56c-111">You cannot specify `Overloads` together with [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) in the same procedure declaration.</span></span>  
  
-   <span data-ttu-id="df56c-112">**Diferenças requeridas.**</span><span class="sxs-lookup"><span data-stu-id="df56c-112">**Required Differences.**</span></span> <span data-ttu-id="df56c-113">O *assinatura* nessa declaração deve ser diferente da assinatura de toda propriedade ou procedimento que ela sobrecarrega.</span><span class="sxs-lookup"><span data-stu-id="df56c-113">The *signature* in this declaration must be different from the signature of every property or procedure that it overloads.</span></span> <span data-ttu-id="df56c-114">A assinatura inclui o nome de propriedade ou procedimento junto com o seguinte:</span><span class="sxs-lookup"><span data-stu-id="df56c-114">The signature comprises the property or procedure name together with the following:</span></span>  
  
    -   <span data-ttu-id="df56c-115">o número de parâmetros</span><span class="sxs-lookup"><span data-stu-id="df56c-115">the number of parameters</span></span>  
  
    -   <span data-ttu-id="df56c-116">a ordem dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="df56c-116">the order of the parameters</span></span>  
  
    -   <span data-ttu-id="df56c-117">os tipos de dados dos parâmetros</span><span class="sxs-lookup"><span data-stu-id="df56c-117">the data types of the parameters</span></span>  
  
    -   <span data-ttu-id="df56c-118">o número de parâmetros de tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="df56c-118">the number of type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="df56c-119">o tipo de retorno (somente para um procedimento de operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="df56c-119">the return type (only for a conversion operator procedure)</span></span>  
  
     <span data-ttu-id="df56c-120">Todas as sobrecargas devem ter o mesmo nome, mas cada uma deve diferir de todas as outras em uma ou mais dentre as condições citadas.</span><span class="sxs-lookup"><span data-stu-id="df56c-120">All overloads must have the same name, but each must differ from all the others in one or more of the preceding respects.</span></span> <span data-ttu-id="df56c-121">Isso permite que o compilador distinguir qual versão usar quando o código chama o procedimento ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="df56c-121">This allows the compiler to distinguish which version to use when code calls the property or procedure.</span></span>  
  
-   <span data-ttu-id="df56c-122">**Diferenças não permitidas.**</span><span class="sxs-lookup"><span data-stu-id="df56c-122">**Disallowed Differences.**</span></span> <span data-ttu-id="df56c-123">Alterar um ou mais dos procedimentos a seguir não é válido para sobrecarga de propriedade ou procedimento, porque eles não fazem parte da assinatura:</span><span class="sxs-lookup"><span data-stu-id="df56c-123">Changing one or more of the following is not valid for overloading a property or procedure, because they are not part of the signature:</span></span>  
  
    -   <span data-ttu-id="df56c-124">Se ele retorna um valor (para um procedimento)</span><span class="sxs-lookup"><span data-stu-id="df56c-124">whether or not it returns a value (for a procedure)</span></span>  
  
    -   <span data-ttu-id="df56c-125">o tipo de dados do valor de retorno (exceto para um operador de conversão)</span><span class="sxs-lookup"><span data-stu-id="df56c-125">the data type of the return value (except for a conversion operator)</span></span>  
  
    -   <span data-ttu-id="df56c-126">os nomes dos parâmetros ou parâmetros de tipo</span><span class="sxs-lookup"><span data-stu-id="df56c-126">the names of the parameters or type parameters</span></span>  
  
    -   <span data-ttu-id="df56c-127">as restrições nos parâmetros do tipo (para um procedimento genérico)</span><span class="sxs-lookup"><span data-stu-id="df56c-127">the constraints on the type parameters (for a generic procedure)</span></span>  
  
    -   <span data-ttu-id="df56c-128">palavras-chave de modificador de parâmetro (como `ByRef` ou `Optional`)</span><span class="sxs-lookup"><span data-stu-id="df56c-128">parameter modifier keywords (such as `ByRef` or `Optional`)</span></span>  
  
    -   <span data-ttu-id="df56c-129">palavras-chave modificadores de propriedade ou um procedimento (como `Public` ou `Shared`)</span><span class="sxs-lookup"><span data-stu-id="df56c-129">property or procedure modifier keywords (such as `Public` or `Shared`)</span></span>  
  
-   <span data-ttu-id="df56c-130">**Modificador opcional.**</span><span class="sxs-lookup"><span data-stu-id="df56c-130">**Optional Modifier.**</span></span> <span data-ttu-id="df56c-131">Você não precisa usar o `Overloads` modificador quando você está definindo várias propriedades ou procedimentos sobrecarregados na mesma classe.</span><span class="sxs-lookup"><span data-stu-id="df56c-131">You do not have to use the `Overloads` modifier when you are defining multiple overloaded properties or procedures in the same class.</span></span> <span data-ttu-id="df56c-132">No entanto, se você usar `Overloads` em uma das declarações, você deve usá-lo em todas elas.</span><span class="sxs-lookup"><span data-stu-id="df56c-132">However, if you use `Overloads` in one of the declarations, you must use it in all of them.</span></span>  
  
-   <span data-ttu-id="df56c-133">**Sombreamento e sobrecarga.**</span><span class="sxs-lookup"><span data-stu-id="df56c-133">**Shadowing and Overloading.**</span></span> <span data-ttu-id="df56c-134">`Overloads`também pode ser usado para sombrear um membro existente, ou conjunto de membros sobrecarregados, em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="df56c-134">`Overloads` can also be used to shadow an existing member, or set of overloaded members, in a base class.</span></span> <span data-ttu-id="df56c-135">Quando você usa `Overloads` dessa forma, você declara a propriedade ou método com o mesmo nome e a mesma lista de parâmetros como membro da classe base, e você não fornecer o `Shadows` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="df56c-135">When you use `Overloads` in this way, you declare the property or method with the same name and the same parameter list as the base class member, and you do not supply the `Shadows` keyword.</span></span>  
  
 <span data-ttu-id="df56c-136">Se você usar `Overrides`, o compilador adiciona implicitamente `Overloads` para que sua biblioteca de APIs trabalhar mais facilmente com o c#.</span><span class="sxs-lookup"><span data-stu-id="df56c-136">If you use `Overrides`, the compiler implicitly adds `Overloads` so that your library APIs work with C# more easily.</span></span>  
  
 <span data-ttu-id="df56c-137">O `Overloads` modificador pode ser usado nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="df56c-137">The `Overloads` modifier can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="df56c-138">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="df56c-138">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="df56c-139">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="df56c-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="df56c-140">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="df56c-140">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="df56c-141">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="df56c-141">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="df56c-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df56c-142">See Also</span></span>  
 <span data-ttu-id="df56c-143">[Sombras](../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="df56c-143">[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="df56c-144"> [Sobrecarga de procedimento](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="df56c-144"> [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span></span>  
<span data-ttu-id="df56c-145"> [Tipos genéricos no Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="df56c-145"> [Generic Types in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
<span data-ttu-id="df56c-146"> [Procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="df56c-146"> [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md) </span></span>  
<span data-ttu-id="df56c-147"> [Como definir um operador de conversão](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)</span><span class="sxs-lookup"><span data-stu-id="df56c-147"> [How to: Define a Conversion Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)</span></span>
