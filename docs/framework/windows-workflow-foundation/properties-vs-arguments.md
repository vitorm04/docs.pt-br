---
title: Propriedades vs. Arguments
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14651389-4a49-4cbb-9ddf-c83fdc155df1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1b9083ecd147a1247209b272dfd1d7b0e3c74f2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="properties-vs-arguments"></a>Propriedades vs. Arguments
Há várias opções disponíveis para passar dados em uma atividade. Além de usar de <xref:System.Activities.InArgument>, as atividades também podem ser desenvolvidas que recebem dados usando propriedades padrão de CLR ou propriedades públicas de <xref:System.Activities.ActivityAction> . Este tópico discute como selecionar o tipo apropriado do método.  
  
## <a name="using-clr-properties"></a>Usando propriedades de CLR  
 Para passar dados em uma atividade, as propriedades de CLR (isto é, os métodos públicos que usam conseguem e definem rotinas para expor dados) são a opção que tem a maioria de restrições. O valor de um parâmetro passado em uma propriedade de CLR deve ser conhecido quando a solução é criado; esse valor será o mesmo para cada instância de fluxo de trabalho. Dessa forma, um valor passado em uma propriedade de CLR é semelhante a uma constante definida no código; esse valor não pode mudar durante a vida útil de atividade, e não pode ser alterado para instâncias diferentes de atividade. <xref:System.Activities.Expressions.InvokeMethod%601.MethodName%2A> é um exemplo de uma propriedade de CLR exposta por uma atividade; o nome do método que a atividade chama não pode ser alterado com base em condições de tempo de execução, e será o mesmo para cada instância de atividade.  
  
## <a name="using-arguments"></a>Usando argumentos  
 Os argumentos devem ser usados quando os dados são avaliados apenas uma vez durante o tempo de vida de atividade; isto é, o valor não será alterado durante o tempo de vida da atividade, mas o valor pode ser diferente para instâncias diferentes de atividade. <xref:System.Activities.Statements.If.Condition%2A> é um exemplo de um valor que seja avaliada; uma vez portanto é definido como um argumento. <xref:System.Activities.Statements.WriteLine.Text%2A> é um exemplo de um método que deve ser definido como um argumento, desde que é avaliado apenas uma vez durante a execução da atividade, mas pode ser diferente para instâncias diferentes de atividade.  
  
## <a name="using-activityaction"></a>Usando ActivityAction  
 Quando os dados precisam ser avaliado várias vezes durante o tempo de vida de execução de uma atividade, <xref:System.Activities.ActivityAction> deve ser usado. Por exemplo, a propriedade de <xref:System.Activities.Statements.While.Condition%2A> é avaliada para cada iteração do loop de <xref:System.Activities.Statements.While> . Se <xref:System.Activities.InArgument> foi usado para essa finalidade, o loop nunca sairia, como o argumento não seria reavaliado para cada iteração, e retornaria sempre o mesmo resultado.
