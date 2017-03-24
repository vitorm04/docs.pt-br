---
title: "(Visual Basic) de espaço de pilha | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID28
dev_langs:
- VB
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6343767da28ea4e02f9443006b222640755f7882
ms.lasthandoff: 03/13/2017

---
# <a name="out-of-stack-space-visual-basic"></a>Sem espaço na pilha (Visual Basic)
A pilha é uma área de trabalho de memória aumenta e diminui dinamicamente com as demandas do seu programa em execução. Os limites foram excedidos.  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se os procedimentos não estão aninhados muito profundamente.  
  
2.  Certifique-se de procedimentos recursivos encerrar corretamente.  
  
3.  Se as variáveis locais exigem mais espaço de variável local que está disponível, tente declarar algumas variáveis no nível de módulo. Você também pode declarar todas as variáveis no procedimento estático precedendo o `Property`, `Sub`, ou `Function` a palavra-chave `Static`. Ou você pode usar o `Static` instrução Declare variáveis estáticas individuais dentro de procedimentos.  
  
4.  Redefina algumas das suas cadeias de caracteres de comprimento fixo como cadeias de caracteres de comprimento variável, como cadeias de caracteres de comprimento fixo usam mais espaço de pilha que cadeias de caracteres de comprimento variável. Você também pode definir a cadeia de caracteres no nível de módulo em que ele requer que nenhum espaço de pilha.  
  
5.  Verifique o número de aninhada `DoEvents` chamadas de função, usando o `Calls` caixa de diálogo exibe quais procedimentos estão ativos na pilha.  
  
6.  Certificar-se de que você não causa uma cascata"eventos" Disparando um evento que chama um procedimento de evento já na pilha. Cascata de eventos é semelhante a uma chamada de procedimento não finalizada recursiva, mas é menos óbvio, desde que a chamada é feita por [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] em vez de uma chamada explícita no código. Use o `Calls`caixa de diálogo exibe quais procedimentos estão ativos na pilha.  
  
## <a name="see-also"></a>Consulte também  
 [Janelas de Memória](https://docs.microsoft.com/visualstudio/debugger/memory-windows)
