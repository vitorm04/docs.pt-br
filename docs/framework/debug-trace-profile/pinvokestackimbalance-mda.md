---
title: MDA pInvokeStackImbalance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b33a3edc5780ecf07e7809ca327a304d748110f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="pinvokestackimbalance-mda"></a>MDA pInvokeStackImbalance
O MDA (Assistente de Depuração Gerenciado) de `pInvokeStackImbalance` é ativado quando o CLR detecta que a profundidade da pilha após uma chamada de invocação de plataforma não corresponde à profundidade da pilha esperada, dada a convenção de chamada especificada no atributo <xref:System.Runtime.InteropServices.DllImportAttribute>, bem como a declaração dos parâmetros na assinatura gerenciada.  
  
> [!NOTE]
>  O MDA `pInvokeStackImbalance` é implementado somente para plataformas x86 de 32 bits.  
  
> [!NOTE]
>  No .NET Framework versão 3.5, o MDA `pInvokeStackImbalance` é desabilitado por padrão. Quando você usar a versão 3.5 do .NET Framework com Visual Studio 2005, o MDA de `pInvokeStackImbalance` aparecerá na lista **Assistentes de Depuração Gerenciados** na caixa de diálogo **Exceções** (que é exibida quando você clica em **Exceções** no menu **Depurar**). No entanto, marcar ou desmarcar a caixa de seleção **Geradas** para `pInvokeStackImbalance` não habilita nem desabilita o MDA, apenas controla se o Visual Studio gera ou não uma exceção quando o MDA é ativado.  
  
## <a name="symptoms"></a>Sintomas  
 Um aplicativo encontra uma violação de acesso ou uma corrupção de memória ao fazer uma chamada de invocação de plataforma ou em seguida a ela.  
  
## <a name="cause"></a>Causa  
 A assinatura gerenciada da chamada de invocação de plataforma pode não corresponder à assinatura não gerenciada do método que está sendo chamado.  Essa incompatibilidade pode ser causada devido à assinatura gerenciada não declarar o número correto de parâmetros ou não especificar o tamanho apropriado para eles.  O MDA também pode ser ativado porque a convenção de chamada, possivelmente especificada pelo atributo <xref:System.Runtime.InteropServices.DllImportAttribute>, não corresponde à convenção de chamada não gerenciada.  
  
## <a name="resolution"></a>Resolução  
 Examine a assinatura de invocação e convenção de chamada da plataforma gerenciada para confirmar que ela corresponde à assinatura e convenção de chamada do destino nativo.  Tente especificar explicitamente a convenção de chamada tanto no lado gerenciado quanto no não gerenciado. Também é possível, embora mais improvável, que a função não gerenciada tenha desequilibrado a pilha por algum outro motivo, assim como um bug no compilador não gerenciado.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Força todas as chamadas de invocação de plataforma a usar o caminho não otimizado no CLR.  
  
## <a name="output"></a>Saída  
 A mensagem MDA fornece o nome da chamada de método de invocação de plataforma que está causando o desequilíbrio na pilha.  Uma mensagem de exemplo de uma chamada de invocação de plataforma no método `SampleMethod` é:  
  
```  
A call to PInvoke function 'SampleMethod' has unbalanced the stack.   
This is likely because the managed PInvoke signature does not match   
the unmanaged target signature. Check that the calling convention and   
parameters of the PInvoke signature match the target unmanaged signature.  
```  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeStackImbalance />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
