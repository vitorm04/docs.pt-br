---
title: MDA reportAvOnComRelease
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f0ecb05dba70dc9c8aba7f04928fd0ab49c900c8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61873945"
---
# <a name="reportavoncomrelease-mda"></a>MDA reportAvOnComRelease
O MDA (Assistente para Depuração Gerenciada) do `reportAvOnComRelease` é ativado quando as exceções são lançadas por causa da contagem de erros pela referência do usuário durante a realização da interoperabilidade COM e do uso do método <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinado com chamadas COM brutas.  
  
## <a name="symptoms"></a>Sintomas  
 Violações de acesso e corrupção de memória.  
  
## <a name="cause"></a>Causa  
 Às vezes, uma exceção é lançada por causa da contagem de erros pela referência do usuário durante a realização da interoperabilidade COM e do uso do método <xref:System.Runtime.InteropServices.Marshal.Release%2A> ou <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> combinado com chamadas COM brutas. Normalmente, essa exceção é descartada porque deixar de fazer isso causaria uma violação de acesso no CLR, desativando-o. Quando esse assistente é habilitado, essas exceções podem ser detectadas e relatadas em vez de ser simplesmente descartadas.  
  
## <a name="resolution"></a>Resolução  
 Examine o código de contagem de referência e procure erros, também examine os clientes nativos do objeto em busca de erros de contagem de referência.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Há dois modos disponíveis. Se o atributo `allowAv` for `true`, o assistente evitará que o tempo de execução descarte a violação de acesso. Se `allowAv` for `false` (o padrão), o tempo de execução descartará a violação de acesso, mas uma mensagem de aviso será relatada ao usuário para indicar que uma exceção foi lançada e descartada.  
  
## <a name="output"></a>Saída  
 Se possível, a saída contém a vtable original do ponteiro da interface COM. Do contrário, é exibida uma mensagem informativa.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
