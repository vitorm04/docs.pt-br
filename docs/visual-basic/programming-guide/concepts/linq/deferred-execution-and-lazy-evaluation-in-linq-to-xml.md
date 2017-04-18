---
title: "Adiado de execução e avaliação lenta em LINQ to XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3b7318eb9853d633d152b93fafcf9570ccd03835
ms.lasthandoff: 03/13/2017


---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>Execução adiada e avaliação lenta em LINQ to XML (Visual Basic)
As operações de consulta e eixo são geralmente implementadas para usar a execução adiada. Este tópico explica os requisitos e as vantagens da execução adiada, além de algumas considerações sobre a implementação.  
  
## <a name="deferred-execution"></a>Execução Adiada  
 Execução adiada significa que a avaliação de uma expressão é atrasada até o seu *percebeu* valor seja realmente necessário. A execução adiada pode aumentar muito o desempenho quando você precisa manipular grandes coleções de dados, especialmente em programas que contêm uma série de consultas ou manipulações encadeadas. Na melhor das hipóteses, a execução adiada permite apenas uma única iteração pela coleção de origem.  
  
 As tecnologias LINQ fazem uso extensivo de execução adiada em ambos os membros do núcleo <xref:System.Linq?displayProperty=fullName>classes e métodos de extensão nos diversos namespaces LINQ, como <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</xref:System.Xml.Linq.Extensions?displayProperty=fullName> </xref:System.Linq?displayProperty=fullName>  
  
## <a name="eager-vs-lazy-evaluation"></a>Avaliação ansiosa vs. lenta  
 Quando você escreve um método que implementa a execução adiada, também precisa decidir se deve implementar o método usando a avaliação lenta ou a avaliação ansiosa.  
  
-   Em *avaliação lenta*, um único elemento da coleção de origem é processado durante cada chamada ao iterador. Essa é a forma comum de implementação de iteradores.  
  
-   Em *avaliação rápida*, a primeira chamada ao iterador resultará em toda a coleção que está sendo processada. Uma cópia temporária da coleção de origem também pode ser necessária. Por exemplo, o <xref:System.Linq.Enumerable.OrderBy%2A>método precisa classificar toda a coleção antes de retornar o primeiro elemento.</xref:System.Linq.Enumerable.OrderBy%2A>  
  
 A avaliação lenta normalmente gera um melhor desempenho porque distribui a sobrecarga de processamento uniformemente por toda a avaliação da coleção e minimiza o uso de dados temporários. Naturalmente, para algumas operações, não há nenhuma outra opção que não seja materializar resultados intermediários.  
  
## <a name="next-steps"></a>Próximas etapas  
 O próximo tópico deste tutorial ilustra a execução adiada:  
  
-   [Exemplo de execução adiada (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Consulte também  
 [Tutorial: Adiada execução (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)   
 [Conceitos e terminologia (transformação funcional) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)   
 [Operações de agregação (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
