---
title: "Estrutura &quot;&lt;structurename&gt;&quot; deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como &quot;Custom&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30941
- vbc30941
dev_langs:
- VB
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
caps.latest.revision: 9
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
ms.openlocfilehash: 67009a75928943ae9b79743ea3ff46e042023a7e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="structure-39ltstructurenamegt39-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-39custom39"></a><span data-ttu-id="6cc5f-102">Estrutura '&lt;structurename&gt;' deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como 'Custom'</span><span class="sxs-lookup"><span data-stu-id="6cc5f-102">Structure &#39;&lt;structurename&gt;&#39; must contain at least one instance member variable or at least one instance event declaration not marked &#39;Custom&#39;</span></span>
<span data-ttu-id="6cc5f-103">Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.</span><span class="sxs-lookup"><span data-stu-id="6cc5f-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="6cc5f-104">Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (não compartilhada), em vez de para todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="6cc5f-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="6cc5f-105">Não compartilhados constantes, propriedades e procedimentos não atender a esse requisito.</span><span class="sxs-lookup"><span data-stu-id="6cc5f-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="6cc5f-106">Além disso, se houver há variáveis não compartilhadas e apenas um evento não compartilhado, este evento não pode ser um `Custom` eventos.</span><span class="sxs-lookup"><span data-stu-id="6cc5f-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="6cc5f-107">**ID do erro:** BC30941</span><span class="sxs-lookup"><span data-stu-id="6cc5f-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6cc5f-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6cc5f-108">To correct this error</span></span>  
  
-   <span data-ttu-id="6cc5f-109">Defina pelo menos uma variável ou evento que não é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="6cc5f-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="6cc5f-110">Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.</span><span class="sxs-lookup"><span data-stu-id="6cc5f-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc5f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6cc5f-111">See Also</span></span>  
 <span data-ttu-id="6cc5f-112">[Estruturas](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="6cc5f-112">[Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="6cc5f-113"> [Como: declarar uma estrutura](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span><span class="sxs-lookup"><span data-stu-id="6cc5f-113"> [How to: Declare a Structure](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md) </span></span>  
<span data-ttu-id="6cc5f-114"> [Instrução Structure](../../../visual-basic/language-reference/statements/structure-statement.md)</span><span class="sxs-lookup"><span data-stu-id="6cc5f-114"> [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)</span></span>
