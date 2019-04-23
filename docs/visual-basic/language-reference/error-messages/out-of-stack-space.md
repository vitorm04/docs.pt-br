---
title: Sem espaço na pilha (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: 29dbdf74808fc98bb856483c3fd8e3a09a72113b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318787"
---
# <a name="out-of-stack-space-visual-basic"></a>Sem espaço na pilha (Visual Basic)
A pilha é uma área de trabalho de memória que aumenta e diminui dinamicamente com as demandas do seu programa em execução. Seus limites forem excedidos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se os procedimentos não estão aninhados muito profundamente.  
  
2. Certifique-se de procedimentos recursivos encerrar corretamente.  
  
3. Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarar algumas variáveis no nível de módulo. Você também pode declarar todas as variáveis no procedimento estático, precedendo o `Property`, `Sub`, ou `Function` palavra-chave with `Static`. Ou você pode usar o `Static` declaração para declarar variáveis estáticas individuais dentro de procedimentos.  
  
4. Redefina algumas das suas cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, como cadeias de caracteres de comprimento fixo usam mais espaço de pilha que cadeias de caracteres de comprimento variável. Você também pode definir a cadeia de caracteres no nível de módulo em que ele requer que nenhum espaço de pilha.  
  
5. Verifique o número de aninhados `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.  
  
6. Verifique se que você não causou uma cascata"eventos" Disparando um evento que chama um procedimento de evento já na pilha. Cascata de eventos é semelhante a uma chamada de procedimento recursivo não terminado, mas é menos óbvio, já que a chamada é feita pelo Visual Basic, em vez de uma chamada explícita no código. Use o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.  
  
## <a name="see-also"></a>Consulte também

- [Janelas de Memória](/visualstudio/debugger/memory-windows)
