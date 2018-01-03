---
title: MDA invalidVariant
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f97fb7f9bdb144f2b586c387f33211734f664eb0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="invalidvariant-mda"></a>MDA invalidVariant
O MDA (Assistente de Depuração Gerenciado) de `invalidVariant` é ativado quando uma estrutura `VARIANT` inválida é encontrada durante uma chamada de código não gerenciado ou nativo para código gerenciado.  
  
## <a name="symptoms"></a>Sintomas  
 Um comportamento inesperado durante a transição entre código nativo e gerenciado que envolve o marshaling de um `VARIANT` para um objeto.  
  
## <a name="cause"></a>Causa  
 Código nativo está passando uma estrutura `VARIANT` malformada para código gerenciado.  O tempo de execução tenta realizar marshaling dessa `VARIANT` para um objeto e ativa o MDA se o `VARIANT` não é válido. Exemplos de `VARIANT`S inválidos incluem um `VARIANT` com `VARTYPE` VT_EMPTY &#124; VT_BYREF ou um `VARIANT` com `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Resolução  
 O código não gerenciado ou nativo passando o `VARIANT` deve garantir que o `VARIANT` seja corretamente formado e inicializado.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 O MDA não tem nenhum efeito sobre o comportamento do tempo de execução.  
  
## <a name="output"></a>Saída  
 Uma mensagem MDA indicando que o tempo de execução detectou inválido `VARIANT` passado para código gerenciado por um módulo não gerenciado.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
