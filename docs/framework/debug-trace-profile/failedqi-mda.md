---
title: MDA failedQI
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 60fd5c29f716aa55f35c520794fbc9a0f673b9f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387166"
---
# <a name="failedqi-mda"></a>MDA failedQI
O MDA (assistente para depuração gerenciada) `failedQI` é ativado quando o tempo de execução chama `QueryInterface` em um ponteiro de interface COM em nome de um RCW (Runtime Callable Wrapper) e a chamada `QueryInterface` falha.  
  
## <a name="symptoms"></a>Sintomas  
 Uma conversão em um RCW falha ou uma chamada ao COM em um RCW falha inesperadamente.  
  
## <a name="cause"></a>Causa  
  
-   A chamada é feita do contexto incorreto.  
  
-   O proxy registrado está falhando a chamada `QueryInterface` porque houve uma tentativa de realizar a chamada no contexto incorreto.  
  
-   Um proxy de propriedade do OLE retornou uma falha HRESULT.  
  
## <a name="resolution"></a>Resolução  
 Consulte a documentação do MSDN sobre as regras do COM.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Se uma chamada `QueryInterface` falhar, o contexto será alternado e haverá uma tentativa de realizar a chamada `QueryInterface` novamente para ver se um contexto incorreto estava com uma falha.  
  
## <a name="output"></a>Saída  
 O nome gerenciado da interface, o GUID da interface e o HRESULT da falha.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
