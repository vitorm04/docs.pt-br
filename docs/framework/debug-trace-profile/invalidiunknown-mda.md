---
title: MDA invalidIUnknown
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="invalidiunknown-mda"></a>MDA invalidIUnknown
O MDA (Assistente de Depuração Gerenciado) de `invalidIUnknown` é ativado quando um ponteiro `IUnknown` inválido é passado do código nativo para o código gerenciado. O `IUnknown` falha em retornar êxito quando consultado para a interface `IUnknown`.  
  
## <a name="symptoms"></a>Sintomas  
 Um erro inesperado ocorre ao fazer marshaling de um ponteiro de interface COM durante o marshaling de argumento.  
  
## <a name="cause"></a>Causa  
 Uma implementação de `QueryInterface` incorreta na interface COM passada para o CLR.  
  
## <a name="resolution"></a>Resolução  
 Corrija a implementação de `QueryInterface`.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR.  
  
## <a name="output"></a>Saída  
 A descrição do erro.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
