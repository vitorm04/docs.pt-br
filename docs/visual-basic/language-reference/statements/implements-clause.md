---
title: "Implementa a cláusula (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ImplementsClause
dev_langs:
- VB
helpviewer_keywords:
- interface implementation, reimplementation
- interface members, reimplementation
- interface members, Implements keyword
- interface members
- members, reimplementation
- interface implementation, Implements keyword
- interface members, implementing
- Implements keyword
- Implements statement, about Implements
- members, implementing
- members, Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
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
ms.openlocfilehash: 2043f432e5179eff9287569075425df2c978702e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="0be2c-102">Cláusula Implements (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0be2c-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="0be2c-103">Indica que um membro de classe ou estrutura está fornecendo a implementação para um membro definido em uma interface.</span><span class="sxs-lookup"><span data-stu-id="0be2c-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0be2c-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="0be2c-104">Remarks</span></span>  
 <span data-ttu-id="0be2c-105">O `Implements` palavra-chave não é igual a [instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0be2c-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="0be2c-106">Você usa o `Implements` para especificar que uma classe ou estrutura implementa uma ou mais interfaces, e, em seguida, para cada membro que você usar o `Implements` palavra-chave para especificar qual interface e qual membro ele implementa.</span><span class="sxs-lookup"><span data-stu-id="0be2c-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>  
  
 <span data-ttu-id="0be2c-107">Se uma classe ou estrutura implementa uma interface, ela deve incluir a `Implements` instrução imediatamente após o [instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) ou [declaração de estrutura](../../../visual-basic/language-reference/statements/structure-statement.md), e ela deve implementar todos os membros definidos pela interface.</span><span class="sxs-lookup"><span data-stu-id="0be2c-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>  
  
## <a name="reimplementation"></a><span data-ttu-id="0be2c-108">Reimplementação</span><span class="sxs-lookup"><span data-stu-id="0be2c-108">Reimplementation</span></span>  
 <span data-ttu-id="0be2c-109">Em uma classe derivada, você pode reimplementar um membro de interface que a classe base já tenha implementado.</span><span class="sxs-lookup"><span data-stu-id="0be2c-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="0be2c-110">Isso é diferente de substituir o membro da classe base nos seguintes aspectos:</span><span class="sxs-lookup"><span data-stu-id="0be2c-110">This is different from overriding the base class member in the following respects:</span></span>  
  
-   <span data-ttu-id="0be2c-111">O membro da classe base não precisa ser [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) para ser reimplementado.</span><span class="sxs-lookup"><span data-stu-id="0be2c-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>  
  
-   <span data-ttu-id="0be2c-112">Você pode reimplementar o membro com um nome diferente.</span><span class="sxs-lookup"><span data-stu-id="0be2c-112">You can reimplement the member with a different name.</span></span>  
  
 <span data-ttu-id="0be2c-113">O `Implements` palavra-chave pode ser usada nesses contextos:</span><span class="sxs-lookup"><span data-stu-id="0be2c-113">The `Implements` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="0be2c-114">Instrução Event</span><span class="sxs-lookup"><span data-stu-id="0be2c-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="0be2c-115">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="0be2c-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="0be2c-116">Instrução Property</span><span class="sxs-lookup"><span data-stu-id="0be2c-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="0be2c-117">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="0be2c-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="0be2c-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0be2c-118">See Also</span></span>  
 <span data-ttu-id="0be2c-119">[Instrução Implements](../../../visual-basic/language-reference/statements/implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0be2c-119">[Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md) </span></span>  
<span data-ttu-id="0be2c-120"> [Instrução interface](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0be2c-120"> [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="0be2c-121"> [Instrução Class](../../../visual-basic/language-reference/statements/class-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0be2c-121"> [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) </span></span>  
<span data-ttu-id="0be2c-122"> [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0be2c-122"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)</span></span>
