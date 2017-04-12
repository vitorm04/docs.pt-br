---
title: Desempenho de consultas encadeadas (LINQ to XML) (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 589f2adc-69f9-404d-b9d6-4c28dabea7f7
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: dd5b63f255107c5864108cfbb87bef6e53a971a0
ms.lasthandoff: 03/13/2017


---
# <a name="performance-of-chained-queries-linq-to-xml-visual-basic"></a>Desempenho de consultas encadeadas (LINQ to XML) (Visual Basic)
Um dos benefícios mais importantes LINQ (e LINQ to XML) é que as consultas encadeadas podem executar bem como uma única consulta maior, mais complicada.  
  
 Uma consulta encadeada é uma consulta que usa outra consulta como sua fonte. Por exemplo, o seguinte código simples, `query2` tem `query1` como sua fonte:  
  
```vb  
Dim root As New XElement("Root", New XElement("Child", 1), New XElement("Child", 2), New XElement("Child", 3), New XElement("Child", 4))  
  
Dim query1 = From x In root.Elements("Child") Where CInt(x) >= 3x  
  
Dim query2 = From e In query1 Where CInt(e) Mod 2 = 0e  
  
For Each i As var In query2  
    Console.WriteLine("{0}", CInt(i))  
Next  
  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
4  
```  
  
 Esta consulta encadeada fornece o mesmo perfil de desempenho que iterando através de uma lista vinculada.  
  
-   O <xref:System.Xml.Linq.XContainer.Elements%2A>eixo tem essencialmente o mesmo desempenho que Iterando através de uma lista vinculada.</xref:System.Xml.Linq.XContainer.Elements%2A> <xref:System.Xml.Linq.XContainer.Elements%2A>é implementado como um iterador com execução adiada.</xref:System.Xml.Linq.XContainer.Elements%2A> Isso significa que faz qualquer trabalho adicional a iterar através da lista vinculada, como alocar do objeto de iterador e manter controle de estado de execução. Este trabalho pode ser dividida em duas categorias: o trabalho que é feito no momento no iterador é configurado, e o trabalho que é feito em cada iteração. O trabalho de configuração é uma pequena quantidade, fixa de trabalho e o trabalho feito em cada iteração é proporcionalmente para o número de itens na coleção de origem.  
  
-   Em `query1`, o `Where` cláusula faz com que a consulta chamar o <xref:System.Linq.Enumerable.Where%2A>método.</xref:System.Linq.Enumerable.Where%2A> Esse método também é implementado como um iterador. O trabalho de configuração consiste em criar uma instância do representante que fará referência a expressão lambda, mais a configuração normal para um iterador. A cada iteração, o representante é chamado para executar o predicado. O trabalho de configuração e trabalho feitos em cada iteração são semelhantes ao trabalho feito para iterar através do eixo.  
  
-   Em `query1`, a cláusula select faz com que a consulta chamar o <xref:System.Linq.Enumerable.Select%2A>método.</xref:System.Linq.Enumerable.Select%2A> Esse método tem o mesmo perfil de desempenho que o <xref:System.Linq.Enumerable.Where%2A>método.</xref:System.Linq.Enumerable.Where%2A>  
  
-   Em `query2`, a cláusula de `Where` e a cláusula `Select` têm o mesmo perfil de desempenho que em `query1`.  
  
 A interação com `query2` é portanto diretamente proporcionalmente para o número de itens na fonte da primeira consulta, ou ser uma das vezes.  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
