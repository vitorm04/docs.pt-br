---
title: "Diferenças entre sombreamento e sobreposição (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- shadowing, vs. overriding
- overriding, vs. shadowing
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: 24
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
ms.openlocfilehash: d37c78550c10cfc7fd4175fbc966fc4e567b6f61
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-shadowing-and-overriding-visual-basic"></a><span data-ttu-id="86108-102">Diferenças entre sombreamento e sobreposição (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="86108-102">Differences Between Shadowing and Overriding (Visual Basic)</span></span>
<span data-ttu-id="86108-103">Quando você define uma classe que herda de uma classe base, às vezes você deseja redefinir uma ou mais dos elementos de classe base na classe derivada.</span><span class="sxs-lookup"><span data-stu-id="86108-103">When you define a class that inherits from a base class, you sometimes want to redefine one or more of the base class elements in the derived class.</span></span> <span data-ttu-id="86108-104">Sombreamento e sobreposição estão disponíveis para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="86108-104">Shadowing and overriding are both available for this purpose.</span></span>  
  
## <a name="comparison"></a><span data-ttu-id="86108-105">Comparação</span><span class="sxs-lookup"><span data-stu-id="86108-105">Comparison</span></span>  
 <span data-ttu-id="86108-106">Sombreamento e sobreposição forem usadas quando uma classe derivada herda de uma classe base, e os dois redefinem um elemento declarado com outro.</span><span class="sxs-lookup"><span data-stu-id="86108-106">Shadowing and overriding are both used when a derived class inherits from a base class, and both redefine one declared element with another.</span></span> <span data-ttu-id="86108-107">Mas há diferenças significativas entre os dois.</span><span class="sxs-lookup"><span data-stu-id="86108-107">But there are significant differences between the two.</span></span>  
  
 <span data-ttu-id="86108-108">A tabela a seguir compara sombreamento com substituição.</span><span class="sxs-lookup"><span data-stu-id="86108-108">The following table compares shadowing with overriding.</span></span>  
  
||||  
|---|---|---|  
|<span data-ttu-id="86108-109">Ponto de comparação</span><span class="sxs-lookup"><span data-stu-id="86108-109">Point of comparison</span></span>|<span data-ttu-id="86108-110">Sombreamento</span><span class="sxs-lookup"><span data-stu-id="86108-110">Shadowing</span></span>|<span data-ttu-id="86108-111">Substituindo</span><span class="sxs-lookup"><span data-stu-id="86108-111">Overriding</span></span>|  
|<span data-ttu-id="86108-112">Finalidade</span><span class="sxs-lookup"><span data-stu-id="86108-112">Purpose</span></span>|<span data-ttu-id="86108-113">Protege contra uma modificação subsequente de classe base que introduz um membro que você já tenha definido em sua classe derivada</span><span class="sxs-lookup"><span data-stu-id="86108-113">Protects against a subsequent base-class modification that introduces a member you have already defined in your derived class</span></span>|<span data-ttu-id="86108-114">Permite polimorfismo através da definição de uma implementação de um procedimento ou propriedade com a mesma sequência de chamada<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86108-114">Achieves polymorphism by defining a different implementation of a procedure or property with the same calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="86108-115">Elemento redefinido</span><span class="sxs-lookup"><span data-stu-id="86108-115">Redefined element</span></span>|<span data-ttu-id="86108-116">Qualquer tipo de elemento declarado</span><span class="sxs-lookup"><span data-stu-id="86108-116">Any declared element type</span></span>|<span data-ttu-id="86108-117">Somente um procedimento (`Function`, `Sub`, ou `Operator`) ou propriedade</span><span class="sxs-lookup"><span data-stu-id="86108-117">Only a procedure (`Function`, `Sub`, or `Operator`) or property</span></span>|  
|<span data-ttu-id="86108-118">Elemento redefinido</span><span class="sxs-lookup"><span data-stu-id="86108-118">Redefining element</span></span>|<span data-ttu-id="86108-119">Qualquer tipo de elemento declarado</span><span class="sxs-lookup"><span data-stu-id="86108-119">Any declared element type</span></span>|<span data-ttu-id="86108-120">Somente um procedimento ou propriedade com a sequência de chamada idêntica<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="86108-120">Only a procedure or property with the identical calling sequence<sup>1</sup></span></span>|  
|<span data-ttu-id="86108-121">Nível de acesso do elemento redefinido</span><span class="sxs-lookup"><span data-stu-id="86108-121">Access level of redefining element</span></span>|<span data-ttu-id="86108-122">Qualquer nível de acesso</span><span class="sxs-lookup"><span data-stu-id="86108-122">Any access level</span></span>|<span data-ttu-id="86108-123">Não é possível alterar o nível de acesso de elemento substituído</span><span class="sxs-lookup"><span data-stu-id="86108-123">Cannot change access level of overridden element</span></span>|  
|<span data-ttu-id="86108-124">Legibilidade de gravabilidade do elemento redefinido</span><span class="sxs-lookup"><span data-stu-id="86108-124">Readability and writability of redefining element</span></span>|<span data-ttu-id="86108-125">Qualquer combinação</span><span class="sxs-lookup"><span data-stu-id="86108-125">Any combination</span></span>|<span data-ttu-id="86108-126">Não é possível mudar a legibilidade ou gravabilidade de propriedades sobrescritas</span><span class="sxs-lookup"><span data-stu-id="86108-126">Cannot change readability or writability of overridden property</span></span>|  
|<span data-ttu-id="86108-127">Controle da redefinição</span><span class="sxs-lookup"><span data-stu-id="86108-127">Control over redefining</span></span>|<span data-ttu-id="86108-128">Elemento de classe base não pode forçar ou proibir sombreamento</span><span class="sxs-lookup"><span data-stu-id="86108-128">Base class element cannot enforce or prohibit shadowing</span></span>|<span data-ttu-id="86108-129">Elemento da classe base pode especificar `MustOverride`, `NotOverridable`, ou`Overridable`</span><span class="sxs-lookup"><span data-stu-id="86108-129">Base class element can specify `MustOverride`, `NotOverridable`, or `Overridable`</span></span>|  
|<span data-ttu-id="86108-130">Uso da palavra-chave</span><span class="sxs-lookup"><span data-stu-id="86108-130">Keyword usage</span></span>|<span data-ttu-id="86108-131">`Shadows`recomendado na classe derivada; `Shadows` pressuposto se nenhum `Shadows` nem `Overrides` especificado<sup>2</sup></span><span class="sxs-lookup"><span data-stu-id="86108-131">`Shadows` recommended in derived class; `Shadows` assumed if neither `Shadows` nor `Overrides` specified<sup>2</sup></span></span>|<span data-ttu-id="86108-132">`Overridable`ou `MustOverride` necessário na classe base; `Overrides` necessário na classe derivada</span><span class="sxs-lookup"><span data-stu-id="86108-132">`Overridable` or `MustOverride` required in base class; `Overrides` required in derived class</span></span>|  
|<span data-ttu-id="86108-133">Herança do elemento redefinido em classes derivadas da classe derivada</span><span class="sxs-lookup"><span data-stu-id="86108-133">Inheritance of redefining element by classes deriving from your derived class</span></span>|<span data-ttu-id="86108-134">Elemento de sombreamento herdado por futuras classes derivadas; elemento sombreado ainda ocultado<sup>3</sup></span><span class="sxs-lookup"><span data-stu-id="86108-134">Shadowing element inherited by further derived classes; shadowed element still hidden<sup>3</sup></span></span>|<span data-ttu-id="86108-135">Substituir o elemento herdado por futuras classes derivadas; elemento sobrescrito ainda sobrescrito</span><span class="sxs-lookup"><span data-stu-id="86108-135">Overriding element inherited by further derived classes; overridden element still overridden</span></span>|  
  
 <span data-ttu-id="86108-136"><sup>1</sup> o *sequência de chamada* consiste em tipo de elemento (`Function`, `Sub`, `Operator`, ou `Property`), nome, listas de parâmetros e tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="86108-136"><sup>1</sup> The *calling sequence* consists of the element type (`Function`, `Sub`, `Operator`, or `Property`), name, parameter list, and return type.</span></span> <span data-ttu-id="86108-137">Você não pode substituir um procedimento com uma propriedade, ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="86108-137">You cannot override a procedure with a property, or the other way around.</span></span> <span data-ttu-id="86108-138">Você não pode substituir um tipo de procedimento (`Function`, `Sub`, ou `Operator`) com outro tipo.</span><span class="sxs-lookup"><span data-stu-id="86108-138">You cannot override one kind of procedure (`Function`, `Sub`, or `Operator`) with another kind.</span></span>  
  
 <span data-ttu-id="86108-139"><sup>2</sup> se você não especificar `Shadows` ou `Overrides`, o compilador emite uma mensagem de aviso para ajudá-lo a não se esqueça de que tipo de redefinição que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="86108-139"><sup>2</sup> If you do not specify either `Shadows` or `Overrides`, the compiler issues a warning message to help you be sure which kind of redefinition you want to use.</span></span> <span data-ttu-id="86108-140">Se você ignorar o aviso, o mecanismo de sombreamento é usado.</span><span class="sxs-lookup"><span data-stu-id="86108-140">If you ignore the warning, the shadowing mechanism is used.</span></span>  
  
 <span data-ttu-id="86108-141"><sup>3</sup> se o elemento sombreador é inacessível numa futura classe derivada, sombreamento não é herdado.</span><span class="sxs-lookup"><span data-stu-id="86108-141"><sup>3</sup> If the shadowing element is inaccessible in a further derived class, shadowing is not inherited.</span></span> <span data-ttu-id="86108-142">Por exemplo, se você declarar o elemento sombreador como `Private`, uma classe que deriva da classe derivada herda ou elemento original em vez do elemento de sombreamento.</span><span class="sxs-lookup"><span data-stu-id="86108-142">For example, if you declare the shadowing element as `Private`, a class deriving from your derived class inherits the original element instead of the shadowing element.</span></span>  
  
## <a name="guidelines"></a><span data-ttu-id="86108-143">Diretrizes</span><span class="sxs-lookup"><span data-stu-id="86108-143">Guidelines</span></span>  
 <span data-ttu-id="86108-144">Você normalmente usa substituindo nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="86108-144">You normally use overriding in the following cases:</span></span>  
  
-   <span data-ttu-id="86108-145">Você está definindo classes derivadas polimórficas.</span><span class="sxs-lookup"><span data-stu-id="86108-145">You are defining polymorphic derived classes.</span></span>  
  
-   <span data-ttu-id="86108-146">Você deseja a segurança de fazer o compilador forçar o mesmo tipo de elemento e sequência de chamada.</span><span class="sxs-lookup"><span data-stu-id="86108-146">You want the safety of having the compiler enforce the identical element type and calling sequence.</span></span>  
  
 <span data-ttu-id="86108-147">Você normalmente usa sombreamento nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="86108-147">You normally use shadowing in the following cases:</span></span>  
  
-   <span data-ttu-id="86108-148">Você prevê que sua classe base pode ser modificada e define um elemento usando o mesmo nome que o seu.</span><span class="sxs-lookup"><span data-stu-id="86108-148">You anticipate that your base class might be modified and define an element using the same name as yours.</span></span>  
  
-   <span data-ttu-id="86108-149">Você quer a liberdade de alterar o tipo de elemento ou sequência de chamada.</span><span class="sxs-lookup"><span data-stu-id="86108-149">You want the freedom of changing the element type or calling sequence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86108-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="86108-150">See Also</span></span>  
 <span data-ttu-id="86108-151">[Referências a elementos declarados](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span><span class="sxs-lookup"><span data-stu-id="86108-151">[References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md) </span></span>  
<span data-ttu-id="86108-152"> [Sombreamento no Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span><span class="sxs-lookup"><span data-stu-id="86108-152"> [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md) </span></span>  
<span data-ttu-id="86108-153"> [Como: ocultar uma variável com o mesmo nome que sua variável](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) </span><span class="sxs-lookup"><span data-stu-id="86108-153"> [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) </span></span>  
<span data-ttu-id="86108-154"> [Como: ocultar uma variável herdada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md) </span><span class="sxs-lookup"><span data-stu-id="86108-154"> [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md) </span></span>  
<span data-ttu-id="86108-155"> [Como: acessar uma variável ocultada por uma classe derivada](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md) </span><span class="sxs-lookup"><span data-stu-id="86108-155"> [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md) </span></span>  
<span data-ttu-id="86108-156"> [Sombras](../../../../visual-basic/language-reference/modifiers/shadows.md) </span><span class="sxs-lookup"><span data-stu-id="86108-156"> [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md) </span></span>  
<span data-ttu-id="86108-157"> [Substituições](../../../../visual-basic/language-reference/modifiers/overrides.md)</span><span class="sxs-lookup"><span data-stu-id="86108-157"> [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)</span></span>
