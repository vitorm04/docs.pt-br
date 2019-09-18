---
title: MDA illegalPrepareConstrainedRegion
ms.date: 03/30/2017
helpviewer_keywords:
- PrepareConstrainedRegions method
- managed debugging assistants (MDAs), illegal PrepareConstrainedRegions
- try/catch exception handling, managed debugging assistants
- IllegalPrepareConstrainedRegions MDA
- MDAs (managed debugging assistants), illegal PrepareConstrainedRegions
ms.assetid: 2f9b5031-f910-4e01-a196-f89eab313eaf
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623aff91eb801b4b32fc180bd97ed3822ad7f163
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052672"
---
# <a name="illegalprepareconstrainedregion-mda"></a>MDA illegalPrepareConstrainedRegion
O MDA (Assistente de Depuração Gerenciado) de `illegalPrepareConstrainedRegion` é ativado quando uma chamada de método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A?displayProperty=nameWithType> não precede imediatamente a instrução `try` do manipulador de exceção. Essa restrição é em nível de MSIL, portanto, é possível ter uma origem não geradora de código entre a chamada e o `try`, assim como comentários.  
  
## <a name="symptoms"></a>Sintomas  
 Uma região de execução restrita (CER) que nunca é tratada como tal, mas como uma bloco de tratamento de exceção simples (`finally` ou `catch`). Como consequência, a região não é executada no caso de uma condição de falta de memória ou uma anulação de thread.  
  
## <a name="cause"></a>Causa  
 O padrão de preparação para uma CER não é seguido corretamente.  Isso é um evento de erro. A <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> chamada de método usada para marcar manipuladores de exceção como introdução a uma `catch` CER em seus `fault` `filter` / `finally` / / blocos deve ser usada imediatamente antes do `try` instrução.  
  
## <a name="resolution"></a>Resolução  
 Certifique-se de que a chamada para <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A> ocorre imediatamente antes da instrução `try`.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 O MDA exibe o nome do método chamando o método <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>, o deslocamento da MSIL e uma mensagem indicando que a chamada não precede imediatamente o início do bloco try.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <illegalPrepareConstrainedRegion/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra o padrão que faz com que esse MDA seja ativado.  
  
```csharp
void MethodWithInvalidPCR()  
{  
    RuntimeHelpers.PrepareConstrainedRegions();  
    Object o = new Object();  
    try  
    {  
        …  
    }  
    finally  
    {  
        …  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareConstrainedRegions%2A>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../interop/interop-marshaling.md)
