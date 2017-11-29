---
title: Solucionando problemas de manipuladores de eventos herdados no Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e8f0b669566bbee6530931bfba9808fad0c085
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="117a8-102">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="117a8-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="117a8-103">Este tópico lista os problemas comuns que surgem com manipuladores de evento nos componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="117a8-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="117a8-104">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="117a8-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="117a8-105">Código no manipulador de eventos é executado duas vezes para cada chamada</span><span class="sxs-lookup"><span data-stu-id="117a8-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="117a8-106">Um manipulador de eventos herdados não deve incluir um [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="117a8-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="117a8-107">O método na classe base já está associado ao evento e disparam adequadamente.</span><span class="sxs-lookup"><span data-stu-id="117a8-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="117a8-108">Remover o `Handles` cláusula do método herdado.</span><span class="sxs-lookup"><span data-stu-id="117a8-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="117a8-109">Se o método herdado não tem um `Handles` palavra-chave, verifique se seu código não contém um extra [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou todos os métodos adicionais que lidam com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="117a8-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="117a8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="117a8-110">See Also</span></span>  
 [<span data-ttu-id="117a8-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="117a8-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
