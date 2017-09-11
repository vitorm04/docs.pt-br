---
title: "Nome de fonte especificado em EventLogSource está registrado em um log diferente do especificado em EventLogName | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
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
ms.openlocfilehash: 17d82bc0b70cac73d21cf9304b3df2b354351ce3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="ef691-102">Nome de fonte especificado em EventLogSource está registrado em um log diferente do especificado em EventLogName</span><span class="sxs-lookup"><span data-stu-id="ef691-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>
<span data-ttu-id="ef691-103">O `EventLog` está tentando fazer referência a uma fonte que está registrada em um log diferente.</span><span class="sxs-lookup"><span data-stu-id="ef691-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="ef691-104">Se você está escrevendo entradas para um log de eventos, você deve especificar o <xref:System.Diagnostics.EventLog.Source%2A>propriedade.</xref:System.Diagnostics.EventLog.Source%2A></span><span class="sxs-lookup"><span data-stu-id="ef691-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="ef691-105">O <xref:System.Diagnostics.EventLog.Source%2A>propriedade registra seu componente com o log de eventos como uma fonte válida de entradas.</xref:System.Diagnostics.EventLog.Source%2A></span><span class="sxs-lookup"><span data-stu-id="ef691-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="ef691-106">Uma única fonte pode ser associado (e, portanto, gravar entradas para) apenas um log de eventos por vez.</span><span class="sxs-lookup"><span data-stu-id="ef691-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="ef691-107">Por padrão, se você tentar gravar uma entrada sem primeiro ter registrado o componente como uma fonte válida, o sistema automaticamente registra a fonte com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A>a propriedade como a cadeia de caracteres de origem.</xref:System.Diagnostics.EventLog.Source%2A></span><span class="sxs-lookup"><span data-stu-id="ef691-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ef691-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ef691-108">To correct this error</span></span>  
  
-   <span data-ttu-id="ef691-109">Verifique se que a fonte é registrada no log correto.</span><span class="sxs-lookup"><span data-stu-id="ef691-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="ef691-110">Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A>método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica exclusivamente o componente para o log de eventos.</xref:System.Diagnostics.EventLog.CreateEventSource%2A></span><span class="sxs-lookup"><span data-stu-id="ef691-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef691-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef691-111">See Also</span></span>  
 <span data-ttu-id="ef691-112">[Administração de Logs de eventos](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18) </span><span class="sxs-lookup"><span data-stu-id="ef691-112">[Administering Event Logs](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18) </span></span>  
<span data-ttu-id="ef691-113"> [Referências de Log de eventos](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87) </span><span class="sxs-lookup"><span data-stu-id="ef691-113"> [Event Log References](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87) </span></span>  
<span data-ttu-id="ef691-114"> [Como: adicionar o aplicativo como uma fonte de entradas de Log de eventos](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c) </span><span class="sxs-lookup"><span data-stu-id="ef691-114"> [How to: Add Your Application as a Source of Event Log Entries](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c) </span></span>  
<span data-ttu-id="ef691-115"> [Como: remover uma fonte de evento](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)</span><span class="sxs-lookup"><span data-stu-id="ef691-115"> [How to: Remove an Event Source](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)</span></span>
