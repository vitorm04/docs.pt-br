---
title: Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409563"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="b39d3-102">Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados</span><span class="sxs-lookup"><span data-stu-id="b39d3-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="b39d3-103">Uma variável declarada com o `Shared` modificador é uma variável compartilhada.</span><span class="sxs-lookup"><span data-stu-id="b39d3-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="b39d3-104">Uma variável compartilhada identifica exatamente um local de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="b39d3-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="b39d3-105">Uma variável declarada com o `WithEvents` modificador afirma que o tipo ao qual a variável pertence trata o conjunto de eventos que a variável gera.</span><span class="sxs-lookup"><span data-stu-id="b39d3-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="b39d3-106">Quando um valor é atribuído à variável, a propriedade criada pela `WithEvents` declaração desvincula qualquer manipulador de eventos existente e conecta o novo manipulador de eventos por meio do `Add` método.</span><span class="sxs-lookup"><span data-stu-id="b39d3-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="b39d3-107">**ID do erro:** BC30594</span><span class="sxs-lookup"><span data-stu-id="b39d3-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b39d3-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b39d3-108">To correct this error</span></span>  
  
- <span data-ttu-id="b39d3-109">Declare seu manipulador de eventos `Shared` .</span><span class="sxs-lookup"><span data-stu-id="b39d3-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b39d3-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="b39d3-110">See also</span></span>

- [<span data-ttu-id="b39d3-111">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="b39d3-111">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="b39d3-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="b39d3-112">WithEvents</span></span>](../modifiers/withevents.md)
