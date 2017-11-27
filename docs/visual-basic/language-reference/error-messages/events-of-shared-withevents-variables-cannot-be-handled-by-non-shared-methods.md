---
title: "Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords: BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="81e1f-102">Eventos de variáveis WithEvents compartilhadas não podem ser identificados por métodos não compartilhados</span><span class="sxs-lookup"><span data-stu-id="81e1f-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="81e1f-103">Uma variável declarada com o `Shared` modificador é uma variável compartilhada.</span><span class="sxs-lookup"><span data-stu-id="81e1f-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="81e1f-104">Uma variável compartilhada identifica exatamente um local de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="81e1f-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="81e1f-105">Uma variável declarada com o `WithEvents` modificador declara que o tipo ao qual pertence a variável trata o conjunto de eventos que a variável gera.</span><span class="sxs-lookup"><span data-stu-id="81e1f-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="81e1f-106">Quando um valor é atribuído à variável, a propriedade criada pelo `WithEvents` declaração desengancha qualquer manipulador de eventos existente e conecta o novo manipulador de eventos por meio de `Add` método.</span><span class="sxs-lookup"><span data-stu-id="81e1f-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="81e1f-107">**ID do erro:** BC30594</span><span class="sxs-lookup"><span data-stu-id="81e1f-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="81e1f-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="81e1f-108">To correct this error</span></span>  
  
-   <span data-ttu-id="81e1f-109">Declarar o manipulador de eventos `Shared`.</span><span class="sxs-lookup"><span data-stu-id="81e1f-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e1f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81e1f-110">See Also</span></span>  
 [<span data-ttu-id="81e1f-111">Compartilhado</span><span class="sxs-lookup"><span data-stu-id="81e1f-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="81e1f-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="81e1f-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
