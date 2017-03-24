---
title: "Outro log de eventos já registrou uma fonte com este nome | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
ms.assetid: e6f5cd95-bb3f-4845-84fb-ae623a9bd44e
caps.latest.revision: 13
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
ms.openlocfilehash: 3f35a9a01b99f88122a594c348eea3feba5e8a8e
ms.lasthandoff: 03/13/2017

---
# <a name="another-event-log-has-already-registered-a-source-with-this-name"></a>Outro log de eventos já registrou uma fonte com este nome
Foi feita uma tentativa para gravar uma entrada em um log de eventos onde a origem especificada é registrada com outro log de eventos.  
  
 Você deve definir a <xref:System.Diagnostics.EventLog.Source%2A>propriedade de sua <xref:System.Diagnostics.EventLog>instância do componente antes de seu componente grava uma entrada para um log.</xref:System.Diagnostics.EventLog> </xref:System.Diagnostics.EventLog.Source%2A> Quando isso acontece, o sistema verifica se a fonte especificada está registrada com o log de eventos para o qual o componente está gravando e chamadas <xref:System.Diagnostics.EventLog.CreateEventSource%2A>se necessário.</xref:System.Diagnostics.EventLog.CreateEventSource%2A>  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Remover a associação da fonte com o primeiro log usando o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>ou o <xref:System.Diagnostics.EventLog.DeleteEventSource%2A>método.</xref:System.Diagnostics.EventLog.DeleteEventSource%2A> </xref:System.Diagnostics.EventLog.DeleteEventSource%2A>  
  
2.  Registre o código-fonte com o novo log.  
  
## <a name="see-also"></a>Consulte também  
 [Objeto My.Application.Log](../../visual-basic/language-reference/objects/my-application-log-object.md)   
 [Como: remover uma fonte de evento](http://msdn.microsoft.com/en-us/bc66c900-4b8a-426a-b8e2-17031a20167e)   
 [Como: adicionar o aplicativo como uma fonte de entradas de Log de eventos](http://msdn.microsoft.com/en-us/948ff920-a739-4e66-a191-ee951512d42c)
