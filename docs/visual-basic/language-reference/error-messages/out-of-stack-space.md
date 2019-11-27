---
title: Espaço em pilha insuficiente
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 9ae604a9727413f2705d42a4b68f5a50b7dd3feb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349190"
---
# <a name="out-of-stack-space-visual-basic"></a>Sem espaço na pilha (Visual Basic)
A pilha é uma área de trabalho de memória que aumenta e diminui dinamicamente com as demandas de seu programa em execução. Seus limites foram excedidos.  
  
## <a name="to-correct-this-error"></a>Para corrigir esse erro  
  
1. Verifique se os procedimentos não estão aninhados muito profundamente.  
  
2. Certifique-se de que os procedimentos recursivos sejam encerrados corretamente.  
  
3. Se variáveis locais exigirem mais espaço de variável local do que o disponível, tente declarar algumas variáveis no nível do módulo. Você também pode declarar todas as variáveis no procedimento estático, precedendo a palavra-chave `Property`, `Sub`ou `Function` com `Static`. Ou você pode usar a instrução `Static` para declarar variáveis estáticas individuais dentro de procedimentos.  
  
4. Redefina algumas das cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, pois as cadeias de caracteres de comprimento fixo usam mais espaço de pilha que as cadeias de caracteres de comprimento variável. Você também pode definir a cadeia de caracteres no nível do módulo, em que ele não requer espaço de pilha.  
  
5. Verifique o número de chamadas de função `DoEvents` aninhadas, usando a caixa de diálogo `Calls` para exibir quais procedimentos estão ativos na pilha.  
  
6. Verifique se você não causou uma "cascata de eventos" disparando um evento que chama um procedimento de evento já na pilha. Uma cascata de eventos é semelhante a uma chamada de procedimento Recursivo não finalizada, mas é menos óbvia, já que a chamada é feita por Visual Basic em vez de uma chamada explícita no código. Use a caixa de diálogo `Calls` para exibir quais procedimentos estão ativos na pilha.  
  
## <a name="see-also"></a>Consulte também

- [Janelas de Memória](/visualstudio/debugger/memory-windows)
