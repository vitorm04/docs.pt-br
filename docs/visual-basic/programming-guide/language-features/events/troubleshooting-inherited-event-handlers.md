---
title: Solucionando problemas de manipuladores de eventos herdados no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053802"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="0dd9f-102">Solucionando problemas de manipuladores de eventos herdados no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0dd9f-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="0dd9f-103">Este tópico lista problemas comuns que surgem com manipuladores de eventos em componentes herdados.</span><span class="sxs-lookup"><span data-stu-id="0dd9f-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="0dd9f-104">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="0dd9f-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="0dd9f-105">Código no manipulador de eventos é executado duas vezes para cada chamada</span><span class="sxs-lookup"><span data-stu-id="0dd9f-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="0dd9f-106">Um manipulador de eventos herdados não deve incluir um [manipula](../../../../visual-basic/language-reference/statements/handles-clause.md) cláusula.</span><span class="sxs-lookup"><span data-stu-id="0dd9f-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="0dd9f-107">O método na classe base já está associado ao evento e será acionado adequadamente.</span><span class="sxs-lookup"><span data-stu-id="0dd9f-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="0dd9f-108">Remover o `Handles` cláusula do método herdado.</span><span class="sxs-lookup"><span data-stu-id="0dd9f-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="0dd9f-109">Se o método herdado não tem um `Handles` palavra-chave, verifique se que seu código não contém um extra [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md) ou todos os métodos adicionais que lidar com o mesmo evento.</span><span class="sxs-lookup"><span data-stu-id="0dd9f-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dd9f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0dd9f-110">See also</span></span>

- [<span data-ttu-id="0dd9f-111">Eventos</span><span class="sxs-lookup"><span data-stu-id="0dd9f-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
