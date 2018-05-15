---
title: Estrutura &#39; &lt;structurename&gt; &#39; deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como &#39;personalizado&#39;
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 85a4babc808e274a99f2c9faf08a02abf8aa4e93
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="69d47-102">Estrutura &#39; &lt;structurename&gt; &#39; deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como &#39;personalizado&#39;</span><span class="sxs-lookup"><span data-stu-id="69d47-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="69d47-103">Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.</span><span class="sxs-lookup"><span data-stu-id="69d47-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="69d47-104">Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (compartilhada), em vez de para todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="69d47-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="69d47-105">Procedimentos, propriedades e constantes não compartilhados não atender a esse requisito.</span><span class="sxs-lookup"><span data-stu-id="69d47-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="69d47-106">Além disso, se não houver nenhum variáveis não compartilhadas e apenas um evento não compartilhado, este evento não pode ser um `Custom` eventos.</span><span class="sxs-lookup"><span data-stu-id="69d47-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="69d47-107">**ID do erro:** BC30941</span><span class="sxs-lookup"><span data-stu-id="69d47-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="69d47-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="69d47-108">To correct this error</span></span>  
  
-   <span data-ttu-id="69d47-109">Defina pelo menos uma variável ou evento que não é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="69d47-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="69d47-110">Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.</span><span class="sxs-lookup"><span data-stu-id="69d47-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69d47-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69d47-111">See Also</span></span>  
 [<span data-ttu-id="69d47-112">Estruturas</span><span class="sxs-lookup"><span data-stu-id="69d47-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="69d47-113">Como declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="69d47-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="69d47-114">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="69d47-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
