---
title: Sem espaço na pilha (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID28
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
ms.openlocfilehash: e39be5913fe877cf7b3396e4f13f4440288cb8f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33593279"
---
# <a name="out-of-stack-space-visual-basic"></a>Sem espaço na pilha (Visual Basic)
A pilha é uma área de trabalho de memória aumenta e diminui dinamicamente com as demandas do seu programa em execução. Os limites foram excedidos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se os procedimentos não estão aninhados muito profundamente.  
  
2.  Certifique-se de procedimentos recursivos encerrar corretamente.  
  
3.  Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarando algumas variáveis no nível de módulo. Também é possível declarar todas as variáveis no procedimento estático precedendo o `Property`, `Sub`, ou `Function` a palavra-chave `Static`. Ou você pode usar o `Static` instrução para declarar variáveis estáticas individuais dentro de procedimentos.  
  
4.  Redefina algumas das suas cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, como cadeias de caracteres de comprimento fixo usam mais espaço de pilha que cadeias de caracteres de comprimento variável. Você também pode definir a cadeia de caracteres no nível de módulo em que ele requer que nenhum espaço de pilha.  
  
5.  Verifique o número de aninhada `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.  
  
6.  Certifique-se de que não causava uma cascata"evento" Disparando um evento que chama um procedimento de evento já na pilha. Cascata de eventos é semelhante a uma chamada de procedimento não finalizada recursiva, mas é menos óbvio, desde que a chamada é feita pelo Visual Basic, em vez de uma chamada explícita no código. Use o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.  
  
## <a name="see-also"></a>Consulte também  
 [Janelas de Memória](/visualstudio/debugger/memory-windows)
