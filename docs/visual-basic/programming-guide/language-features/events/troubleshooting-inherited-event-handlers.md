---
title: Solução de problemas de manipuladores de eventos herdados
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: d228e916e45054bc088aa633afd9d591e592210d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91057995"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="df286-102">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="df286-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>

<span data-ttu-id="df286-103">Este tópico lista os problemas comuns que surgem com manipuladores de eventos em componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="df286-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="df286-104">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="df286-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="df286-105">O código no manipulador de eventos é executado duas vezes para cada chamada</span><span class="sxs-lookup"><span data-stu-id="df286-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="df286-106">Um manipulador de eventos herdado não deve incluir uma cláusula [Handles](../../../language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="df286-106">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="df286-107">O método na classe base já está associado ao evento e será acionado de acordo.</span><span class="sxs-lookup"><span data-stu-id="df286-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="df286-108">Remova a `Handles` cláusula do método herdado.</span><span class="sxs-lookup"><span data-stu-id="df286-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="df286-109">Se o método herdado não tiver uma `Handles` palavra-chave, verifique se o seu código não contém uma [instrução AddHandler](../../../language-reference/statements/addhandler-statement.md) extra ou quaisquer métodos adicionais que manipulem o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="df286-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df286-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="df286-110">See also</span></span>

- [<span data-ttu-id="df286-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="df286-111">Events</span></span>](index.md)
