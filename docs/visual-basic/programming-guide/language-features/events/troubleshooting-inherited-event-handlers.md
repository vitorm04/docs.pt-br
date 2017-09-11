---
title: "Solução de problemas de manipuladores de eventos no Visual Basic herdados | Documentos do Microsoft"
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
- troubleshooting events
- inherited events
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: 11
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
ms.openlocfilehash: f64395975821226d42664bbf78b04120d49a38bc
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="938ec-102">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="938ec-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="938ec-103">Este tópico lista problemas comuns que surgem com manipuladores de evento nos componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="938ec-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="938ec-104">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="938ec-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="938ec-105">O código no manipulador de eventos é executado duas vezes para cada chamada</span><span class="sxs-lookup"><span data-stu-id="938ec-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="938ec-106">Um manipulador de eventos herdados não deve incluir uma [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="938ec-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="938ec-107">O método na classe base já está associado ao evento e acionará adequadamente.</span><span class="sxs-lookup"><span data-stu-id="938ec-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="938ec-108">Remover o `Handles` cláusula do método herdado.</span><span class="sxs-lookup"><span data-stu-id="938ec-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     <span data-ttu-id="938ec-109">[!code-vb[32 VbVbalrEvents](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="938ec-109">[!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]</span></span>  
  
-   <span data-ttu-id="938ec-110">Se o método herdado não tem um `Handles` palavra-chave, verifique se seu código não contém um arquivo extra [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou quaisquer métodos adicionais que tratam o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="938ec-110">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="938ec-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="938ec-111">See Also</span></span>  
 [<span data-ttu-id="938ec-112">Eventos</span><span class="sxs-lookup"><span data-stu-id="938ec-112">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
