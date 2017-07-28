---
title: "Mitigação: chamadas de método EventSource.WriteEvent"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 327a9fdb-ba8e-40f7-89e5-4c89b46e594f
caps.latest.revision: 6
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 270f89183bced5d07598b1731f18acf90ec9715a
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="mitigation-eventsourcewriteevent-method-calls"></a>Mitigação: chamadas de método EventSource.WriteEvent
O [!INCLUDE[net_v451](../../../includes/net-v451-md.md)] impõe um contrato entre um método de evento ETW em uma classe derivada de <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> e o método <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> da sua classe base. O método de evento ETW deve passar o método <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> para a ID do evento seguida dos mesmos argumentos que foram passados para o método de evento.  
  
## <a name="impact"></a>Impacto  
 Um método de evento ETW definido da seguinte maneira interrompe o contrato:  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message, "-");  
}  
```  
  
 Quando esse contrato é violado, uma exceção <xref:System.IndexOutOfRangeException> é acionada no tempo de execução se um objeto <xref:System.Diagnostics.Tracing.EventListener> ler dados <xref:System.Diagnostics.Tracing.EventSource> em processo.  
  
 A definição desse método de evento ETW deve seguir este padrão:  
  
```  
[Event(2, Level = EventLevel.Informational)]  
public void Info2(string message)  
{  
   base.WriteEvent(2, message);  
}  
```  
  
## <a name="mitigation"></a>Redução  
 Você deve modificar o código existente de acordo com o padrão necessário.  
  
 Você pode minimizar o volume de código que precisa alterar definindo dois métodos para chamar o método <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A>, da seguinte forma:  
  
```  
[NonEvent]  
public void Info2(string message)  
{  
   Info2Internal(message, "-");  
}  
  
public void Info2Internal(string message, string prefix)  
{  
   WriteEvent(2, message, prefix);  
}  
```  
  
## <a name="see-also"></a>Consulte também  
 [Alterações no tempo de execução](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-5-1.md)

