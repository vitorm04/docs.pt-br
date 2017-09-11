---
title: "Outro log de eventos já registrou uma fonte com este nome | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 75d16b760437d872758bfa6c97b6c51caf541196
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a><span data-ttu-id="83401-102">Outro log de eventos já registrou uma fonte com este nome</span><span class="sxs-lookup"><span data-stu-id="83401-102">Another event log has already registered a source with this name</span></span>
<span data-ttu-id="83401-103">Foi feita uma tentativa para gravar uma entrada em um log de eventos onde a origem especificada é registrada com outro log de eventos.</span><span class="sxs-lookup"><span data-stu-id="83401-103">An attempt was made to write an entry to an event log where the specified source is registered with another event log.</span></span>  
  
 <span data-ttu-id="83401-104">Você deve definir a <xref:System.Diagnostics.EventLog.Source%2A>propriedade de sua <xref:System.Diagnostics.EventLog>instância do componente antes de seu componente grava uma entrada para um log.</xref:System.Diagnostics.EventLog> </xref:System.Diagnostics.EventLog.Source%2A></span><span class="sxs-lookup"><span data-stu-id="83401-104">You must set the <xref:System.Diagnostics.EventLog.Source%2A> property of your <xref:System.Diagnostics.EventLog> component instance before your component writes an entry to a log.</span></span> <span data-ttu-id="83401-105">Quando isso acontece, o sistema verifica se a fonte especificada está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A>se necessário.</xref:System.Diagnostics.EventLog.CreateEventSource%2A></span><span class="sxs-lookup"><span data-stu-id="83401-105">When this happens, the system checks that the source you specified is registered with the event log to which the component is writing, and calls <xref:System.Diagnostics.EventLog.CreateEventSource%2A> if needed.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="83401-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="83401-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="83401-107">Remover a associação da fonte com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>ou o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>método.</xref:System.Diagnostics.EventLog.DeleteEventSource%2A> </xref:System.Diagnostics.EventLog.DeleteEventSource%2A></span><span class="sxs-lookup"><span data-stu-id="83401-107">Remove the association of the source with the first log using the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> or the <xref:System.Diagnostics.EventLog.DeleteEventSource%2A> method.</span></span>  
  
2.  <span data-ttu-id="83401-108">Registre o código-fonte com o novo log.</span><span class="sxs-lookup"><span data-stu-id="83401-108">Register the source with the new log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83401-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="83401-109">See Also</span></span>  
 <span data-ttu-id="83401-110">[Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md) </span><span class="sxs-lookup"><span data-stu-id="83401-110">[My.Application.Log Object](../../visual-basic/language-reference/objects/my-application-log-object.md) </span></span>  
<span data-ttu-id="83401-111"> [Como: remover uma fonte de evento](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e) </span><span class="sxs-lookup"><span data-stu-id="83401-111"> [How to: Remove an Event Source](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e) </span></span>  
<span data-ttu-id="83401-112"> [Como: adicionar o aplicativo como uma fonte de entradas de Log de eventos](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)</span><span class="sxs-lookup"><span data-stu-id="83401-112"> [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)</span></span>
