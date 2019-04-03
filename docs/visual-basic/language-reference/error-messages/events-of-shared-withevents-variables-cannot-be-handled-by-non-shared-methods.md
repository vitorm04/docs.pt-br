---
title: Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838645"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="dfb6a-102">Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados</span><span class="sxs-lookup"><span data-stu-id="dfb6a-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="dfb6a-103">Uma variável declarada com o `Shared` modificador é uma variável compartilhada.</span><span class="sxs-lookup"><span data-stu-id="dfb6a-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="dfb6a-104">Uma variável compartilhada identifica exatamente um local de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="dfb6a-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="dfb6a-105">Uma variável declarada com o `WithEvents` modificador declara que o tipo ao qual pertence a variável manipula o conjunto de eventos que aciona a variável.</span><span class="sxs-lookup"><span data-stu-id="dfb6a-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="dfb6a-106">Quando um valor é atribuído à variável, a propriedade criada pela `WithEvents` declaração desengancha qualquer manipulador de eventos existente e conecta-se o novo manipulador de eventos por meio de `Add` método.</span><span class="sxs-lookup"><span data-stu-id="dfb6a-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="dfb6a-107">**ID do erro:** BC30594</span><span class="sxs-lookup"><span data-stu-id="dfb6a-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dfb6a-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="dfb6a-108">To correct this error</span></span>  
  
-   <span data-ttu-id="dfb6a-109">Declare o manipulador de eventos `Shared`.</span><span class="sxs-lookup"><span data-stu-id="dfb6a-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb6a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfb6a-110">See also</span></span>

- [<span data-ttu-id="dfb6a-111">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="dfb6a-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="dfb6a-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="dfb6a-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
