---
title: MDA disconnectedContext
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181968"
---
# <a name="disconnectedcontext-mda"></a>MDA disconnectedContext
O MDA (Assistente para depuração gerenciada) `disconnectedContext` é ativado quando o CLR tenta realizar a transição para um apartment ou contexto desconectado durante a manutenção de uma solicitação sobre um objeto COM.  
  
## <a name="symptoms"></a>Sintomas  
 As chamadas feitas em um [RCW](../../../docs/framework/interop/runtime-callable-wrapper.md) (Runtime Callable Wrapper) são entregues ao componente COM subjacente no apartment ou no contexto atual, em vez de aquele no qual elas existem. Isso pode causar corrupção ou perda de dados se o componente COM não for com vários threads, como no caso de componentes STA (Single-Threaded Apartment). Como alternativa, se o RCW em si for um proxy, a chamada pode resultar no lançamento de um <xref:System.Runtime.InteropServices.COMException> com um HRESULT de RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>Causa  
 O apartment ou contexto OLE foi desligado quando o CLR tenta realizar a transição para ele. Isso é comumente causado por apartments STA a serem desligados antes de todos os componentes COM de propriedade do apartment terem sido completamente liberados. Isso pode ocorrer como resultado de uma chamada explícita de um código de usuário em um RCW ou enquanto o CLR em si está manipulando o componente COM, por exemplo, quando o CLR está liberando o componente COM quando o RCW associado passou por coleta de lixo.  
  
## <a name="resolution"></a>Resolução  
 Para evitar esse problema, garanta que o thread que possui o STA não termine antes de o aplicativo ter concluído todos os objetos que residem no apartment. O mesmo se aplica a contextos; garanta que os contextos não desliguem antes de o aplicativo ser totalmente encerrado com qualquer componente COM que resida dentro do contexto.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR. Apenas relata dados sobre o contexto desconectado.  
  
## <a name="output"></a>Saída  
 Relata o cookie de contexto do apartment ou contexto desconectado.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
