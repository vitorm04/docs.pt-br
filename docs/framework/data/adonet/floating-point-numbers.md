---
title: "Números de ponto flutuante"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c218c6-1c44-4402-a167-4f6262629a91
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f041fc4e42d2b1e18ef701cd80396e92e571bff0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="floating-point-numbers"></a>Números de ponto flutuante
Este tópico descreve alguns dos problemas que os desenvolvedores enfrentam com frequência quando elas funcionam com números de ponto flutuante em [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]. Esses problemas são causados pela maneira que computadores armazenam números de ponto flutuante e não são específicas para um provedor específico, como <xref:System.Data.SqlClient> ou <xref:System.Data.OracleClient>.  
  
 Números de ponto flutuante geralmente não têm uma representação binária exata. Em vez disso, o computador armazena uma aproximação do número. Em momentos diferentes, diferentes números de dígitos binários podem ser usados para representar o número. Quando um flutuante número é convertido de uma representação para outra representação, os dígitos menos significantes desse número de ponto pode variar um pouco. Normalmente, a conversão ocorre quando o número é convertido de um tipo em outro tipo. A variação ocorre se a conversão ocorre dentro de um banco de dados entre tipos que representam os valores de banco de dados ou tipos. Devido a essas alterações, números logicamente seria iguais podem ter alterações em seus dígitos menos significativo que fazer com que eles têm valores diferentes. O número de dígitos de precisão no número pode ser maior ou menor que o esperado. Quando formatado como uma cadeia de caracteres, o número não pode mostrar o valor esperado.  
  
 Para minimizar os efeitos, você deve usar a correspondência mais próxima entre tipos numéricos que estão disponíveis para você. Por exemplo, se você estiver trabalhando com [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)], o valor numérico exato pode mudar se você converter um valor de Transact-SQL de tipo real para um valor do tipo float. No [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], converter um <xref:System.Single> para um <xref:System.Double> também pode produzir resultados inesperados. Em ambos os casos, uma boa estratégia é fazer todos os valores no uso de aplicativo o mesmo tipo numérico. Você também pode usar um tipo decimal de precisão fixa ou converter números de ponto flutuante para um tipo decimal de precisão fixa antes de trabalhar com eles.  
  
 Para solucionar problemas com a comparação de igualdade, considere a possibilidade de codificar seu aplicativo, de forma que as variações de dígitos menos significantes são ignoradas. Por exemplo, em vez de comparar para ver se os dois números são iguais, subtrai um número das outras. Se a diferença estiver dentro de uma margem aceitável de arredondamento, seu aplicativo pode tratar os números como se eles são os mesmos.  
  
## <a name="see-also"></a>Consulte também  
 [Por que números de ponto flutuante podem perder a precisão](http://msdn.microsoft.com/library/1acb1add-ac06-4134-a2fd-aff13d8c4c15)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
