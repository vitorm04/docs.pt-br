---
title: MDA dllMainReturnsFalse
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052851"
---
# <a name="dllmainreturnsfalse-mda"></a>MDA dllMainReturnsFalse
O MDA (assistente para depuração gerenciada) `dllMainReturnsFalse` é ativado se a função `DllMain` gerenciada de um assembly de usuário, chamada com o motivo DLL_PROCESS_ATTACH, retorna FALSE.  
  
## <a name="symptoms"></a>Sintomas  
 A função `DllMain` retornou FALSE, indicando que ela não foi executada corretamente. Isso pode causar problemas indeterminados porque as funções `DllMain` normalmente contêm um código de inicialização importante.  
  
## <a name="cause"></a>Causa  
 A função `DllMain` é chamada com o motivo DLL_PROCESS_ATTACH para a inicialização da DLL após o carregamento. Se ela retorna FALSE, isso significa que a inicialização da DLL falhou.  
  
## <a name="resolution"></a>Resolução  
 Analise o código da função `DllMain` da DLL com falha e identifique a causa da falha de inicialização.  
  
## <a name="effect-on-the-runtime"></a>Efeito sobre o tempo de execução  
 Esse MDA não tem efeito sobre o CLR. Ele apenas relata dados sobre o valor retornado de `DllMain`.  
  
## <a name="output"></a>Saída  
 Uma mensagem indicando que uma função `DllMain`, chamada pelo motivo DLL_PROCESS_ATTACH, retornou FALSE. Observe que esse MDA é ativado somente se `DllMain` é implementado no código gerenciado.  
  
## <a name="configuration"></a>Configuração  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Consulte também

- [Diagnosticando erros com Assistentes de Depuração Gerenciados](diagnosing-errors-with-managed-debugging-assistants.md)
