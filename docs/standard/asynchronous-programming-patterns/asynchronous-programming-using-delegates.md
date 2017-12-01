---
title: "Programação assíncrona usando delegados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BeginInvoke method
- asynchronous programming, delegates
- asynchronous delegates
- calling synchronous methods in asynchronous manner
- EndInvoke method
- calling asynchronous methods
- delegates [.NET Framework], asynchronous
- synchronous calling in asynchronous manner
ms.assetid: 38a345ca-6963-4436-9608-5c9defef9c64
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 596d2be26318b782423653b4eb3f43c1f9fc4b92
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="asynchronous-programming-using-delegates"></a>Programação assíncrona usando delegados
Delegados permitem que você chamar um método síncrono de maneira assíncrona. Quando você chama um delegado de forma síncrona, o `Invoke` método chama o método de destino diretamente no thread atual. Se o `BeginInvoke` método é chamado, o common language runtime (CLR) as filas de solicitação e retorna imediatamente ao chamador. O método de destino é chamado de forma assíncrona em um thread do pool de threads. O thread original, que enviou a solicitação, é gratuito continuar a executar em paralelo com o método de destino. Se um método de retorno de chamada foi especificado na chamada para o `BeginInvoke` método, o método de retorno de chamada é chamado quando o método de destino termina. O método de retorno de chamada, o `EndInvoke` método obtém o valor de retorno e os parâmetros de entrada/saída ou somente de saída. Se nenhum método de retorno de chamada é especificado ao chamar `BeginInvoke`, `EndInvoke` pode ser chamado do thread que chamou `BeginInvoke`.  
  
> [!IMPORTANT]
>  Compiladores emitirá classes delegate com `Invoke`, `BeginInvoke`, e `EndInvoke` métodos usando a assinatura do delegado especificada pelo usuário. O `BeginInvoke` e `EndInvoke` métodos devem ser decorados como nativo. Como esses métodos são marcados como nativo, o CLR fornece automaticamente a implementação em tempo de carregamento de classe. O carregador garante que elas não são substituídas.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Chamando métodos síncronos de forma assíncrona](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 Discute o uso de delegates para fazer chamadas para métodos comuns e fornece exemplos de código simples que mostram quatro maneiras para aguardar uma chamada assíncrona retornar.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [EAP (Padrão Assíncrono baseado em Evento)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 Descreve a programação assíncrona com o .NET Framework.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Delegate>
