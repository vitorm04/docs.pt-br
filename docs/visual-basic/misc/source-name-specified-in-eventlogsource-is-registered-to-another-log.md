---
title: Nome da fonte especificado em EventLogSource está registrado em um log diferente daquele especificado em EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 03fcc41b0fbb84233aa037d7af17d168050a98b6
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44261045"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nome da fonte especificado em EventLogSource está registrado em um log diferente daquele especificado em EventLogName
O `EventLog` está tentando fazer referência a uma fonte que está registrada em um log diferente. Se você estiver escrevendo entradas para um log de eventos, você deve especificar o <xref:System.Diagnostics.EventLog.Source%2A> propriedade. O <xref:System.Diagnostics.EventLog.Source%2A> propriedade registra seu componente com o log de eventos como uma fonte válida de entradas. Uma única fonte pode ser associado (e, portanto, gravar entradas) apenas um log de eventos por vez.  
  
 Por padrão, se você tentar gravar uma entrada sem primeiro ter registrado seu componente como uma origem válida, o sistema automaticamente registra o código-fonte com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A> a propriedade como a cadeia de caracteres de origem.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Verifique se que a fonte é registrada no log correto. Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica exclusivamente o seu componente para o log de eventos.  
  
## <a name="see-also"></a>Consulte também  
 [Administrando os Logs de eventos](https://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [Referências de Log de eventos](https://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [Como: adicionar o aplicativo como uma fonte de entradas de Log de eventos](https://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [Como: remover uma fonte de evento](https://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
