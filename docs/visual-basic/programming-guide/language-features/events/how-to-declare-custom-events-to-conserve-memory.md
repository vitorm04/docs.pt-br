---
title: "Como: declarar eventos personalizados para conservar memória (Visual Basic) | Documentos do Microsoft"
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
- declaring events, custom
- events [Visual Basic], custom
- custom events
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
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
ms.openlocfilehash: 130cbda875d6a56f826aefea341d233ea4b3731d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="a45c5-102">Como declarar eventos personalizados para conservar memória (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a45c5-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="a45c5-103">Há várias circunstâncias quando é importante que um aplicativo mantenha seu uso de memória baixa.</span><span class="sxs-lookup"><span data-stu-id="a45c5-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="a45c5-104">Eventos personalizados permitem que o aplicativo use memória somente para os eventos que ele gerencia.</span><span class="sxs-lookup"><span data-stu-id="a45c5-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="a45c5-105">Por padrão, quando uma classe declara um evento, o compilador aloca memória para um campo armazenar as informações do evento.</span><span class="sxs-lookup"><span data-stu-id="a45c5-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="a45c5-106">Se uma classe tem muitos eventos não utilizados, eles desnecessariamente ocupam de memória.</span><span class="sxs-lookup"><span data-stu-id="a45c5-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="a45c5-107">Em vez de usar a implementação padrão de eventos que o Visual Basic fornece, você pode usar eventos personalizados para gerenciar o uso de memória mais cuidadosamente.</span><span class="sxs-lookup"><span data-stu-id="a45c5-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a45c5-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a45c5-108">Example</span></span>  
 <span data-ttu-id="a45c5-109">Neste exemplo, a classe usa uma instância da <xref:System.ComponentModel.EventHandlerList>classe, armazenado no `Events` campo para armazenar informações sobre os eventos em uso.</xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="a45c5-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="a45c5-110">O <xref:System.ComponentModel.EventHandlerList>classe é uma classe lista otimizada projetada para armazenar representantes.</xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="a45c5-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="a45c5-111">Todos os eventos na classe usam o `Events` campo para controlar quais métodos estão manipulando cada evento.</span><span class="sxs-lookup"><span data-stu-id="a45c5-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 <span data-ttu-id="a45c5-112">[!code-vb[VbVbalrEvents&#22;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a45c5-112">[!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a45c5-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a45c5-113">See Also</span></span>  
 <span data-ttu-id="a45c5-114"><xref:System.ComponentModel.EventHandlerList></xref:System.ComponentModel.EventHandlerList></span><span class="sxs-lookup"><span data-stu-id="a45c5-114"><xref:System.ComponentModel.EventHandlerList></span></span>   
<span data-ttu-id="a45c5-115"> [Eventos](../../../../visual-basic/programming-guide/language-features/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="a45c5-115"> [Events](../../../../visual-basic/programming-guide/language-features/events/index.md) </span></span>  
<span data-ttu-id="a45c5-116"> [Como declarar eventos personalizados para evitar bloqueio](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span><span class="sxs-lookup"><span data-stu-id="a45c5-116"> [How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)</span></span>
