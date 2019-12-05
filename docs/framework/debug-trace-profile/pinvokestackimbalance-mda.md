---
title: MDA pInvokeStackImbalance
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- stack depth
- platform invoke stack imbalance
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- PInvokeStackImbalance MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: 34ddc6bd-1675-4f35-86aa-de1645d5c631
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 117e0838f78d43bf9ffa555947bf8749830c9840
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802001"
---
# <a name="pinvokestackimbalance-mda"></a>MDA PInvokeStackImbalance

O `PInvokeStackImbalance` MDA (Assistente de depuração gerenciada) é ativado quando o CLR detecta que a profundidade da pilha após uma chamada de invocação de plataforma não corresponde à profundidade de pilha esperada, dada a Convenção de chamada especificada no atributo <xref:System.Runtime.InteropServices.DllImportAttribute> e a declaração dos parâmetros na assinatura gerenciada.

O MDA `PInvokeStackImbalance` é implementado somente para plataformas x86 de 32 bits.

> [!NOTE]
> O `PInvokeStackImbalance` MDA é desabilitado por padrão. No Visual Studio 2017 e versões posteriores, o `PInvokeStackImbalance` MDA aparece na lista de **assistentes de depuração gerenciada** na caixa de diálogo **configurações de exceção** (que é exibida quando você seleciona **depurar** > **configurações de exceção**do **Windows** > ). No entanto, marcar ou desmarcar a caixa de seleção **interromper quando lançados** não habilitará ou desabilitará o MDA; Ele apenas controla se o Visual Studio lança uma exceção quando o MDA é ativado.

## <a name="symptoms"></a>Sintomas

Um aplicativo encontra uma violação de acesso ou uma corrupção de memória ao fazer uma chamada de invocação de plataforma ou em seguida a ela.

## <a name="cause"></a>Causa

A assinatura gerenciada da chamada de invocação de plataforma pode não corresponder à assinatura não gerenciada do método que está sendo chamado.  Essa incompatibilidade pode ser causada devido à assinatura gerenciada não declarar o número correto de parâmetros ou não especificar o tamanho apropriado para eles.  O MDA também pode ser ativado porque a convenção de chamada, possivelmente especificada pelo atributo <xref:System.Runtime.InteropServices.DllImportAttribute>, não corresponde à convenção de chamada não gerenciada.

## <a name="resolution"></a>Resolução

Examine a assinatura de invocação e convenção de chamada da plataforma gerenciada para confirmar que ela corresponde à assinatura e convenção de chamada do destino nativo.  Tente especificar explicitamente a convenção de chamada tanto no lado gerenciado quanto no não gerenciado. Também é possível, embora mais improvável, que a função não gerenciada tenha desequilibrado a pilha por algum outro motivo, assim como um bug no compilador não gerenciado.

## <a name="effect-on-the-runtime"></a>Efeito sobre o runtime

Força todas as chamadas de invocação de plataforma a usar o caminho não otimizado no CLR.

## <a name="output"></a>Saída

A mensagem MDA fornece o nome da chamada de método de invocação de plataforma que está causando o desequilíbrio na pilha. Uma mensagem de exemplo de uma chamada de invocação de plataforma no método `SampleMethod` é:

**Uma chamada para a função PInvoke ' SampleMethod ' desbalanceou a pilha. Isso é provável porque a assinatura do PInvoke gerenciada não corresponde à assinatura de destino não gerenciada. Verifique se a Convenção de chamada e os parâmetros da assinatura PInvoke correspondem à assinatura não gerenciada de destino.**

## <a name="configuration"></a>Configuração do

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../interop/interop-marshaling.md)
