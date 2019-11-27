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
ms.openlocfilehash: fd2ef1c25233cc1eaad6bcde68923688393b471d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345100"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="a4a78-102">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a4a78-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="a4a78-103">Este tópico lista os problemas comuns que surgem com manipuladores de eventos em componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="a4a78-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a4a78-104">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="a4a78-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="a4a78-105">O código no manipulador de eventos é executado duas vezes para cada chamada</span><span class="sxs-lookup"><span data-stu-id="a4a78-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="a4a78-106">Um manipulador de eventos herdado não deve incluir uma cláusula [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="a4a78-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="a4a78-107">O método na classe base já está associado ao evento e será acionado de acordo.</span><span class="sxs-lookup"><span data-stu-id="a4a78-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="a4a78-108">Remova a cláusula `Handles` do método herdado.</span><span class="sxs-lookup"><span data-stu-id="a4a78-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="a4a78-109">Se o método herdado não tiver uma palavra-chave `Handles`, verifique se o seu código não contém uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) extra ou quaisquer métodos adicionais que manipulem o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="a4a78-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a78-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4a78-110">See also</span></span>

- [<span data-ttu-id="a4a78-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="a4a78-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
