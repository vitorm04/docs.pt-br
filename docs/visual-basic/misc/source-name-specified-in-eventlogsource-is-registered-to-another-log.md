---
title: Nome da fonte especificado em EventLogSource está registrado em um log diferente daquele especificado em EventLogName
ms.date: 07/20/2015
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
ms.openlocfilehash: 22129ab0c4f7fe0a78300907a949d9368028c9fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61594978"
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>Nome da fonte especificado em EventLogSource está registrado em um log diferente daquele especificado em EventLogName
O `EventLog` está tentando fazer referência a uma fonte que está registrada em um log diferente. Se você estiver escrevendo entradas para um log de eventos, você deve especificar o <xref:System.Diagnostics.EventLog.Source%2A> propriedade. O <xref:System.Diagnostics.EventLog.Source%2A> propriedade registra seu componente com o log de eventos como uma fonte válida de entradas. Uma única fonte pode ser associado (e, portanto, gravar entradas) apenas um log de eventos por vez.  
  
 Por padrão, se você tentar gravar uma entrada sem primeiro ter registrado seu componente como uma origem válida, o sistema automaticamente registra o código-fonte com o log de eventos, usando o valor da <xref:System.Diagnostics.EventLog.Source%2A> a propriedade como a cadeia de caracteres de origem.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique se que a fonte é registrada no log correto. Para fazer isso, use o <xref:System.Diagnostics.EventLog.CreateEventSource%2A> método ou uma de suas sobrecargas para especificar uma cadeia de caracteres que identifica exclusivamente o seu componente para o log de eventos.  
  
## <a name="see-also"></a>Consulte também

- [Administrando os Logs de eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/4f69axw4(v=vs.90))
- [Referências de Log de eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k43k9z2a(v=vs.90))
- [Como: Adicionar seu aplicativo como uma fonte de entradas de Log de eventos](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/xz73e171(v=vs.90))
- [Como: Remover uma fonte de evento](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/k57466fc(v=vs.90))
