---
title: Espaço em pilha insuficiente
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: afb6a42372bdbd2e49ac15fbbf2b9e254f8db431
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871317"
---
# <a name="out-of-stack-space-visual-basic"></a>Sem espaço na pilha (Visual Basic)

A pilha é uma área de trabalho de memória que aumenta e diminui dinamicamente com as demandas de seu programa em execução. Seus limites foram excedidos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se os procedimentos não estão aninhados muito profundamente.  
  
2. Certifique-se de que os procedimentos recursivos sejam encerrados corretamente.  
  
3. Se variáveis locais exigirem mais espaço de variável local do que o disponível, tente declarar algumas variáveis no nível do módulo. Você também pode declarar todas as variáveis no procedimento estático precedendo `Property` a `Sub` `Function` palavra-chave, ou com `Static` . Ou você pode usar a `Static` instrução para declarar variáveis estáticas individuais dentro de procedimentos.  
  
4. Redefina algumas das cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, pois as cadeias de caracteres de comprimento fixo usam mais espaço de pilha que as cadeias de caracteres de comprimento variável. Você também pode definir a cadeia de caracteres no nível do módulo, em que ele não requer espaço de pilha.  
  
5. Verifique o número de chamadas de função aninhadas `DoEvents` , usando a `Calls` caixa de diálogo para exibir quais procedimentos estão ativos na pilha.  
  
6. Verifique se você não causou uma "cascata de eventos" disparando um evento que chama um procedimento de evento já na pilha. Uma cascata de eventos é semelhante a uma chamada de procedimento Recursivo não finalizada, mas é menos óbvia, já que a chamada é feita por Visual Basic em vez de uma chamada explícita no código. Use a `Calls` caixa de diálogo para exibir quais procedimentos estão ativos na pilha.  
  
## <a name="see-also"></a>Confira também

- [Janelas de memória](/visualstudio/debugger/memory-windows)
