---
title: Desempenho de consultas encadeadas (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b2f1d715-8946-4dc0-8d56-fb3d1bba54a6
ms.openlocfilehash: dca2fa37a18209c5970172cb084151a58ea4ebc9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336359"
---
# <a name="performance-of-chained-queries-linq-to-xml-c"></a>Desempenho de consultas encadeadas (LINQ to XML) (C#)
Um dos benefícios mais importantes LINQ (e LINQ to XML) é que as consultas encadeadas podem executar bem como uma única consulta maior, mais complicada.  
  
 Uma consulta encadeada é uma consulta que usa outra consulta como sua fonte. Por exemplo, o seguinte código simples, `query2` tem `query1` como sua fonte:  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", 1),  
    new XElement("Child", 2),  
    new XElement("Child", 3),  
    new XElement("Child", 4)  
);  
  
var query1 = from x in root.Elements("Child")  
             where (int)x >= 3  
             select x;  
  
var query2 = from e in query1  
             where (int)e % 2 == 0  
             select e;  
  
foreach (var i in query2)  
    Console.WriteLine("{0}", (int)i);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
4  
```  
  
 Esta consulta encadeada fornece o mesmo perfil de desempenho que iterando através de uma lista vinculada.  
  
-   O eixo de <xref:System.Xml.Linq.XContainer.Elements%2A> tem essencialmente o mesmo desempenho que iterando através de uma lista vinculada. <xref:System.Xml.Linq.XContainer.Elements%2A> é implementado como um iterador com execução adiada. Isso significa que faz qualquer trabalho adicional a iterar através da lista vinculada, como alocar do objeto de iterador e manter controle de estado de execução. Este trabalho pode ser dividida em duas categorias: o trabalho que é feito no momento no iterador é configurado, e o trabalho que é feito em cada iteração. O trabalho de configuração é uma pequena quantidade, fixa de trabalho e o trabalho feito em cada iteração é proporcionalmente para o número de itens na coleção de origem.  
  
-   Em `query1`, a cláusula de `where` faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Where%2A> . Esse método também é implementado como um iterador. O trabalho de configuração consiste em criar uma instância do representante que fará referência a expressão lambda, mais a configuração normal para um iterador. A cada iteração, o representante é chamado para executar o predicado. O trabalho de configuração e trabalho feitos em cada iteração são semelhantes ao trabalho feito para iterar através do eixo.  
  
-   Em `query1`, a cláusula SELECT faz com que a consulta chama o método de <xref:System.Linq.Enumerable.Select%2A> . Este método tem o mesmo perfil de desempenho que o método de <xref:System.Linq.Enumerable.Where%2A> .  
  
-   Em `query2`, a cláusula de `where` e a cláusula `select` têm o mesmo perfil de desempenho que em `query1`.  
  
 A interação com `query2` é portanto diretamente proporcionalmente para o número de itens na fonte da primeira consulta, ou ser uma das vezes. Um exemplo correspondente do Visual Basic terá o mesmo perfil de desempenho.  
  
 Para obter mais informações sobre iteradores, consulte [yield](../../../../csharp/language-reference/keywords/yield.md).  
  
 Para um tutorial mais detalhado sobre o encadeamento de consultas, consulte [Tutorial: encadear consultas juntas (C#)](http://msdn.microsoft.com/library/c08d228a-f07a-4c98-810f-1bf0e8f2257c).  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
