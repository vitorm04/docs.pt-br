---
title: "Eventos de variáveis WithEvents compartilhadas não podem ser manipuladas por métodos não compartilhados | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
dev_langs:
- VB
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
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
ms.openlocfilehash: bfaf62cfa746a173f0b22655168aa60b0fe5373e
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="622df-102">Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados</span><span class="sxs-lookup"><span data-stu-id="622df-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="622df-103">Uma variável declarada com o `Shared` modificador é uma variável compartilhada.</span><span class="sxs-lookup"><span data-stu-id="622df-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="622df-104">Uma variável compartilhada identifica exatamente um local de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="622df-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="622df-105">Uma variável declarada com o `WithEvents` modificador declara o tipo ao qual a variável pertence manipula o conjunto de eventos que a variável gera.</span><span class="sxs-lookup"><span data-stu-id="622df-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="622df-106">Quando um valor é atribuído à variável, a propriedade criada pelo `WithEvents` declaração desengancha qualquer manipulador de eventos existente e conecta o novo manipulador de eventos por meio de `Add` método.</span><span class="sxs-lookup"><span data-stu-id="622df-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="622df-107">**ID do erro:** BC30594</span><span class="sxs-lookup"><span data-stu-id="622df-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="622df-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="622df-108">To correct this error</span></span>  
  
-   <span data-ttu-id="622df-109">Declarar o manipulador de eventos `Shared`.</span><span class="sxs-lookup"><span data-stu-id="622df-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622df-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="622df-110">See Also</span></span>  
 <span data-ttu-id="622df-111">[Compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) </span><span class="sxs-lookup"><span data-stu-id="622df-111">[Shared](../../../visual-basic/language-reference/modifiers/shared.md) </span></span>  
<span data-ttu-id="622df-112"> [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)</span><span class="sxs-lookup"><span data-stu-id="622df-112"> [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)</span></span>
