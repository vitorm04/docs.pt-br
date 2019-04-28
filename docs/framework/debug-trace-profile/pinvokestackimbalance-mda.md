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
ms.openlocfilehash: 9ecdfd708217f260b0c02383159fab88948029c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61874205"
---
# <a name="pinvokestackimbalance-mda"></a>MDA PInvokeStackImbalance

O `PInvokeStackImbalance` Assistente para depuração gerenciada (MDA) é ativado quando o CLR detecta que a profundidade da pilha após uma invocação de plataforma chamada não coincide com a profundidade da pilha esperada, dada a convenção de chamada especificada no <xref:System.Runtime.InteropServices.DllImportAttribute> atributo e o declaração dos parâmetros na assinatura gerenciada.

O MDA `PInvokeStackImbalance` é implementado somente para plataformas x86 de 32 bits.

> [!NOTE]
> O `PInvokeStackImbalance` MDA é desabilitado por padrão. No Visual Studio 2017, o `PInvokeStackImbalance` MDA aparece no **assistentes para depuração gerenciada** lista o **configurações de exceção** caixa de diálogo (que é exibido quando você seleciona **depurar**  >  **Windows** > **configurações de exceção**). No entanto, marcando ou desmarcando as **quebrar quando lançada** caixa de seleção não habilite ou desabilite o MDA; apenas controla se o Visual Studio gera uma exceção quando o MDA é ativado.

## <a name="symptoms"></a>Sintomas

Um aplicativo encontra uma violação de acesso ou uma corrupção de memória ao fazer uma chamada de invocação de plataforma ou em seguida a ela.

## <a name="cause"></a>Causa

A assinatura gerenciada da chamada de invocação de plataforma pode não corresponder à assinatura não gerenciada do método que está sendo chamado.  Essa incompatibilidade pode ser causada devido à assinatura gerenciada não declarar o número correto de parâmetros ou não especificar o tamanho apropriado para eles.  O MDA também pode ser ativado porque a convenção de chamada, possivelmente especificada pelo atributo <xref:System.Runtime.InteropServices.DllImportAttribute>, não corresponde à convenção de chamada não gerenciada.

## <a name="resolution"></a>Resolução

Examine a assinatura de invocação e convenção de chamada da plataforma gerenciada para confirmar que ela corresponde à assinatura e convenção de chamada do destino nativo.  Tente especificar explicitamente a convenção de chamada tanto no lado gerenciado quanto no não gerenciado. Também é possível, embora mais improvável, que a função não gerenciada tenha desequilibrado a pilha por algum outro motivo, assim como um bug no compilador não gerenciado.

## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução

Força todas as chamadas de invocação de plataforma a usar o caminho não otimizado no CLR.

## <a name="output"></a>Saída

A mensagem MDA fornece o nome da chamada de método de invocação de plataforma que está causando o desequilíbrio na pilha. Uma mensagem de exemplo de uma chamada de invocação de plataforma no método `SampleMethod` é:

**Uma chamada para a função PInvoke 'SampleMethod' tem tenha desequilibrado a pilha. Isso provavelmente ocorre porque a assinatura gerenciada de PInvoke não coincide com a assinatura de destino não gerenciado. Verifique se a convenção de chamada e os parâmetros da assinatura PInvoke correspondem a assinatura não gerenciada de destino.**

## <a name="configuration"></a>Configuração

```xml
<mdaConfig>
  <assistants>
    <pInvokeStackImbalance />
  </assistants>
</mdaConfig>
```

## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnosticando erros com Assistentes de Depuração Gerenciados](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling de interoperabilidade](../../../docs/framework/interop/interop-marshaling.md)
