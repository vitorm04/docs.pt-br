---
title: MDA marshalCleanupError
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c78fedaab26ff7f1da7bccd98c83a90e550d9014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="marshalcleanuperror-mda"></a>MDA marshalCleanupError
O MDA (assistente de depuração gerenciado) do `marshalCleanupError` é ativado quando o CLR (Common Language Runtime) encontra um erro ao tentar limpar estruturas temporárias e a memória usada para realizar marshaling de tipos de dados entre limites de código gerenciado e nativo.  
  
## <a name="symptoms"></a>Sintomas  
 A perda de memória ocorre em transações de código gerenciado e nativo, no estado de tempo de execução, como quando a cultura de thread não é restaurada ou quando há um erro na limpeza de <xref:System.Runtime.InteropServices.SafeHandle>.  
  
## <a name="cause"></a>Causa  
 Ocorreu um erro inesperado durante a limpeza das estruturas temporárias.  
  
## <a name="resolution"></a>Resolução  
 Verifique se há erro em todas as implementações do destruidor, do finalizador e do marshaler personalizado <xref:System.Runtime.InteropServices.SafeHandle>.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 Uma mensagem que indica que a operação falhou durante a limpeza.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
