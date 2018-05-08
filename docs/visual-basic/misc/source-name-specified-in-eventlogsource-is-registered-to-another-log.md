---
title: Nome da fonte especificado em EventLogSource está registrado em um log que não seja especificado em EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: dc4c8f212de61a304f04c81d81d2e75c490450ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nome da fonte especificado em EventLogSource está registrado em um log que não seja especificado em EventLogName
O `EventLog` está tentando fazer referência a uma fonte que é registrada em um log diferente. Se você está escrevendo entradas para um log de eventos, você deve especificar o <xref:System.Diagnostics.EventLog.Source%2A> propriedade. O <xref:System.Diagnostics.EventLog.Source%2A> propriedade registra seu componente com o log de eventos como uma fonte válida de entradas. Uma única fonte pode ser associado (e, portanto, gravar entradas para) apenas um log de eventos por vez.  
  
 Por padrão, se você tentar gravar uma entrada sem primeiro ter registrado seu componente como uma origem válida, o sistema automaticamente registra o código-fonte com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A> a propriedade como a cadeia de caracteres de origem.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se que a fonte está registrada no log correto. Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica exclusivamente o seu componente ao log de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Administração de Logs de eventos](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Referências de Log de eventos](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Como: adicionar o aplicativo como uma fonte de entradas de Log de eventos](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [Como: remover uma fonte de evento](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
