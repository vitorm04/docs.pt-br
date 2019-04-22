---
title: A estrutura '<structurename>' deve conter pelos menos uma variável membro da instância ou pelo menos uma declaração de evento da instância não marcada como 'Personalizada'
ms.date: 07/20/2015
f1_keywords:
- bc30941
- vbc30941
helpviewer_keywords:
- BC30941
ms.assetid: 7054cc1e-bac3-4c3d-82f3-35772bd8dd3b
ms.openlocfilehash: 598aef3943a53ee6eb97064819c9128de1839f52
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813932"
---
# <a name="structure-structurename-must-contain-at-least-one-instance-member-variable-or-at-least-one-instance-event-declaration-not-marked-custom"></a><span data-ttu-id="0a6cf-102">Estrutura '\<structurename >' deve conter pelo menos uma variável de membro de instância ou declaração de evento de pelo menos uma instância não marcada como 'Personalizada'</span><span class="sxs-lookup"><span data-stu-id="0a6cf-102">Structure '\<structurename>' must contain at least one instance member variable or at least one instance event declaration not marked 'Custom'</span></span>
<span data-ttu-id="0a6cf-103">Uma definição de estrutura não inclui quaisquer variáveis não compartilhadas ou eventos não personalizados não compartilhados.</span><span class="sxs-lookup"><span data-stu-id="0a6cf-103">A structure definition does not include any nonshared variables or nonshared noncustom events.</span></span>  
  
 <span data-ttu-id="0a6cf-104">Cada estrutura deve ter uma variável ou um evento que se aplica a cada instância específica (não compartilhada) em vez da todas as instâncias coletivamente ([compartilhado](../../../visual-basic/language-reference/modifiers/shared.md)).</span><span class="sxs-lookup"><span data-stu-id="0a6cf-104">Every structure must have either a variable or an event that applies to each specific instance (nonshared) instead of to all instances collectively ([Shared](../../../visual-basic/language-reference/modifiers/shared.md)).</span></span> <span data-ttu-id="0a6cf-105">Não compartilhado de constantes, propriedades e procedimentos não atendem a esse requisito.</span><span class="sxs-lookup"><span data-stu-id="0a6cf-105">Nonshared constants, properties, and procedures do not satisfy this requirement.</span></span> <span data-ttu-id="0a6cf-106">Além disso, se não houver nenhuma variáveis não compartilhadas e apenas um evento não compartilhado, esse evento não pode ser um `Custom` eventos.</span><span class="sxs-lookup"><span data-stu-id="0a6cf-106">In addition, if there are no nonshared variables and only one nonshared event, that event cannot be a `Custom` event.</span></span>  
  
 <span data-ttu-id="0a6cf-107">**ID do erro:** BC30941</span><span class="sxs-lookup"><span data-stu-id="0a6cf-107">**Error ID:** BC30941</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a6cf-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="0a6cf-108">To correct this error</span></span>  
  
-   <span data-ttu-id="0a6cf-109">Defina pelo menos uma variável ou evento que não é `Shared`.</span><span class="sxs-lookup"><span data-stu-id="0a6cf-109">Define at least one variable or event that is not `Shared`.</span></span> <span data-ttu-id="0a6cf-110">Se você definir apenas um evento, ele deve ser não personalizados, bem como não compartilhado.</span><span class="sxs-lookup"><span data-stu-id="0a6cf-110">If you define only one event, it must be noncustom as well as nonshared.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a6cf-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0a6cf-111">See also</span></span>

- [<span data-ttu-id="0a6cf-112">Estruturas</span><span class="sxs-lookup"><span data-stu-id="0a6cf-112">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="0a6cf-113">Como: declarar uma estrutura</span><span class="sxs-lookup"><span data-stu-id="0a6cf-113">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="0a6cf-114">Instrução Structure</span><span class="sxs-lookup"><span data-stu-id="0a6cf-114">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
