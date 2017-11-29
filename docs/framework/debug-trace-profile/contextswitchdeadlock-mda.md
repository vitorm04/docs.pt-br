---
title: MDA contextSwitchDeadlock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deadlocks [.NET Framework]
- pumping messages
- STA message pumping
- single-threaded COM components
- MDAs (managed debugging assistants), context switching deadlocks
- managed debugging assistants (MDAs), context switching deadlocks
- ContextSwitchDeadlock MDA
- message pumping
- context switching deadlocks
ms.assetid: 26dfaa15-9ddb-4b0a-b6da-999bba664fa6
caps.latest.revision: "22"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e67c5c47dbe95d7c2b804f0ae87200db489d0306
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="contextswitchdeadlock-mda"></a>MDA contextSwitchDeadlock
O MDA (assistente para depuração gerenciada) `contextSwitchDeadlock` é ativado quando um deadlock é detectado durante uma tentativa de transição de contexto COM.  
  
## <a name="symptoms"></a>Sintomas  
 O sintoma mais comum é que uma chamada em um componente COM não gerenciado de um código gerenciado não retorna.  Outro sintoma é que o uso da memória aumenta com o tempo.  
  
## <a name="cause"></a>Causa  
 A causa mais provável é que um thread de STA (single-threaded apartment) não está bombeando as mensagens. O thread de STA está esperando sem bombear as mensagens ou está realizando operações longas e não está permitindo o bombeamento da fila de mensagens.  
  
 O aumento do uso da memória com o tempo é causado por uma tentativa do thread do finalizador de chamar `Release` em um componente COM não gerenciado e pela falta de retorno desse componente.  Isso impede que o finalizador recupere outros objetos.  
  
 Por padrão, STA é o modelo de threading para o thread principal dos aplicativos do console do Visual Basic. Esse MDA é ativado se um thread de STA usar a interoperabilidade de COM direta ou indiretamente por meio do Common Language Runtime ou de um controle de terceiros.  Para evitar a ativação desse MDA em um aplicativo do console do Visual Basic, aplique o atributo <xref:System.MTAThreadAttribute> ao método principal ou modifique o aplicativo para bombear as mensagens.  
  
 É possível que esse MDA seja ativado erroneamente quando todas as condições a seguir forem atendidas:  
  
-   Um aplicativo cria componentes COM de threads de STA direta ou indiretamente por meio das bibliotecas.  
  
-   O aplicativo foi interrompido no depurador e o usuário continuou o aplicativo ou realizou uma operação de etapa.  
  
-   A depuração não gerenciada não está habilitada.  
  
 Para determinar se o MDA está sendo ativado erroneamente, desabilite todos os pontos de interrupção, reinicie o aplicativo e permita que ele seja executado sem parar. Se o MDA não for ativado, é provável que a ativação inicial era falsa. Nesse caso, desabilite o MDA para evitar interferências na sessão de depuração.  
  
> [!NOTE]
>  Esse MDA está no conjunto padrão para o [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] e versões mais recentes. Quando o processo de hospedagem é habilitado em [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], não é possível desabilitar MDAs que estão no conjunto padrão. Como é habilitado por padrão, o processo de hospedagem deve ser desabilitado explicitamente. Para obter informações sobre como desabilitar os MDAs, consulte “Habilitando e desabilitando os MDAs” em [Diagnosticando erros com assistentes para depuração gerenciada](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).  
  
## <a name="resolution"></a>Resolução  
 Siga as regras de COM em relação ao bombeamento das mensagens de STA.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR. Ele apenas relata dados sobre contextos de COM.  
  
## <a name="output"></a>Saída  
 Uma mensagem descrevendo o contexto atual e o contexto de destino.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <contextSwitchDeadlock />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
