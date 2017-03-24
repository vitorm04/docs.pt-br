---
title: "Nome de fonte especificado em EventLogSource está registrado em um log diferente do especificado em EventLogName | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 48c31a9cf2e1fe0e20a3b642a58f18b0dbfe7d84
ms.lasthandoff: 03/13/2017

---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nome de fonte especificado em EventLogSource está registrado em um log diferente do especificado em EventLogName
O `EventLog` está tentando fazer referência a uma fonte que está registrada em um log diferente. Se você está escrevendo entradas para um log de eventos, você deve especificar o <xref:System.Diagnostics.EventLog.Source%2A>propriedade.</xref:System.Diagnostics.EventLog.Source%2A> O <xref:System.Diagnostics.EventLog.Source%2A>propriedade registra seu componente com o log de eventos como uma fonte válida de entradas.</xref:System.Diagnostics.EventLog.Source%2A> Uma única fonte pode ser associado (e, portanto, gravar entradas para) apenas um log de eventos por vez.  
  
 Por padrão, se você tentar gravar uma entrada sem primeiro ter registrado o componente como uma fonte válida, o sistema automaticamente registra a fonte com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A>a propriedade como a cadeia de caracteres de origem.</xref:System.Diagnostics.EventLog.Source%2A>  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se que a fonte é registrada no log correto. Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A>método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica exclusivamente o componente para o log de eventos.</xref:System.Diagnostics.EventLog.CreateEventSource%2A>  
  
## <a name="see-also"></a>Consulte também  
 [Administração de Logs de eventos](http://msdn.microsoft.com/en-us/35f53238-bdd2-417b-acd8-2fd9f7397f18)   
 [Referências de Log de eventos](http://msdn.microsoft.com/en-us/4af0661c-6c96-49f4-961d-b26ed9bc3e87)   
 [Como: adicionar o aplicativo como uma fonte de entradas de Log de eventos](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)   
 [Como: remover uma fonte de evento](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)
