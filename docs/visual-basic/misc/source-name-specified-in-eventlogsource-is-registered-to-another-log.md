---
title: O nome da fonte especificado em EventLogSource está registrado em um log diferente daquele especificado em EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 1b577e3b0613001b6241dcfdc59c8c84029197d2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058924"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a><span data-ttu-id="62a92-102">O nome da fonte especificado em EventLogSource está registrado em um log diferente daquele especificado em EventLogName</span><span class="sxs-lookup"><span data-stu-id="62a92-102">Source name specified in EventLogSource is registered to a log other than that specified in EventLogName</span></span>

<span data-ttu-id="62a92-103">O `EventLog` está tentando se referir a uma fonte que está registrada em um log diferente.</span><span class="sxs-lookup"><span data-stu-id="62a92-103">The `EventLog` is attempting to refer to a source that is registered to a different log.</span></span> <span data-ttu-id="62a92-104">Se você estiver gravando entradas em um log de eventos, deverá especificar a <xref:System.Diagnostics.EventLog.Source%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="62a92-104">If you are writing entries to an event log, you must specify the <xref:System.Diagnostics.EventLog.Source%2A> property.</span></span> <span data-ttu-id="62a92-105">A <xref:System.Diagnostics.EventLog.Source%2A> Propriedade registra seu componente com o log de eventos como uma fonte de entradas válida.</span><span class="sxs-lookup"><span data-stu-id="62a92-105">The <xref:System.Diagnostics.EventLog.Source%2A> property registers your component with the event log as a valid source of entries.</span></span> <span data-ttu-id="62a92-106">Uma única fonte pode ser associada (e, portanto, gravar entradas em) apenas um log de eventos por vez.</span><span class="sxs-lookup"><span data-stu-id="62a92-106">A single source can be associated with (and therefore write entries to) only one event log at a time.</span></span>  
  
 <span data-ttu-id="62a92-107">Por padrão, se você tentar gravar uma entrada sem primeiro registrar seu componente como uma fonte válida, o sistema registrará automaticamente a origem com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A> propriedade como a cadeia de caracteres de origem.</span><span class="sxs-lookup"><span data-stu-id="62a92-107">By default, if you try to write an entry without first having registered your component as a valid source, the system automatically registers the source with the event log, using the value of the <xref:System.Diagnostics.EventLog.Source%2A> property as the source string.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62a92-108">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="62a92-108">To correct this error</span></span>  
  
- <span data-ttu-id="62a92-109">Verifique se a origem está registrada no log correto.</span><span class="sxs-lookup"><span data-stu-id="62a92-109">Make sure the source is registered to the correct log.</span></span> <span data-ttu-id="62a92-110">Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica exclusivamente o componente para o log de eventos.</span><span class="sxs-lookup"><span data-stu-id="62a92-110">To do this, use the <xref:System.Diagnostics.EventLog.CreateEventSource%2A> method or one of its overloads to specify a string that uniquely identifies your component to the event log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62a92-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="62a92-111">See also</span></span>

- <span data-ttu-id="62a92-112">[Administrando logs de eventos](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="62a92-112">[Administering Event Logs](/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))</span></span>
- <span data-ttu-id="62a92-113">[Referências do log de eventos](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="62a92-113">[Event Log References](/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))</span></span>
- <span data-ttu-id="62a92-114">[Como: adicionar seu aplicativo como uma fonte de entradas de log de eventos](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="62a92-114">[How to: Add Your Application as a Source of Event Log Entries](/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))</span></span>
- <span data-ttu-id="62a92-115">[Como: remover uma origem do evento](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="62a92-115">[How to: Remove an Event Source](/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))</span></span>
