---
title: MDA invalidVariant
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216267"
---
# <a name="invalidvariant-mda"></a>MDA invalidVariant
O MDA (Assistente de Depuração Gerenciado) de `invalidVariant` é ativado quando uma estrutura `VARIANT` inválida é encontrada durante uma chamada de código não gerenciado ou nativo para código gerenciado.  
  
## <a name="symptoms"></a>Sintomas  
 Um comportamento inesperado durante a transição entre código nativo e gerenciado que envolve o marshaling de um `VARIANT` para um objeto.  
  
## <a name="cause"></a>Causa  
 Código nativo está passando uma estrutura `VARIANT` malformada para código gerenciado.  O runtime tenta realizar marshaling dessa `VARIANT` para um objeto e ativa o MDA se o `VARIANT` não é válido. Exemplos de `VARIANT`S inválidos incluem um `VARIANT` com `VARTYPE` VT_EMPTY &#124; VT_BYREF ou um `VARIANT` com `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Resolução  
 O código não gerenciado ou nativo passando o `VARIANT` deve garantir que o `VARIANT` seja corretamente formado e inicializado.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o runtime  
 O MDA não tem nenhum efeito sobre o comportamento do runtime.  
  
## <a name="output"></a>Saída  
 Uma mensagem MDA indicando que o runtime detectou inválido `VARIANT` passado para código gerenciado por um módulo não gerenciado.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../interop/interop-marshaling.md)
