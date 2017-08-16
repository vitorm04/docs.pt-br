---
title: Objetos XName e XNamespace atomizados (LINQ to XML) (C#) | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: a5b21433-b49d-415c-b00e-bcbfb0d267d7
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 89f5c2634e1deb196b121f2983b85f125927ae32
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017


---
# <a name="atomized-xname-and-xnamespace-objects-linq-to-xml-c"></a>Objetos XName e XNamespace atomizados (LINQ to XML) (C#)
Os objetos <xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> são *atomizados* ou seja, se tiverem o mesmo nome qualificado, referem-se ao mesmo objeto. Este benefícios de desempenho das para consultas: Quando você compara dois nomes atomizados para igualdade, o linguagem intermediária subjacente só precisa determinar se o ponto de duas referências para o mesmo objeto. O código subjacente não tem que fazer as comparações de cadeias de caracteres, que poderiam demoradas.  
  
## <a name="atomization-semantics"></a>Semântica de atomização  
 A atomização significa que se dois objetos <xref:System.Xml.Linq.XName> tiverem o mesmo nome local e estiverem no mesmo namespace, compartilharão a mesma instância. Da mesma forma, se dois objetos <xref:System.Xml.Linq.XNamespace> tiverem o mesmo URI de namespace, compartilharão a mesma instância.  
  
 Para que uma classe permite objetos atomizados, o construtor para a classe deve ser particular, não público. Isso ocorre porque se foi o construtor público, você pode criar um objeto não atomizado. As classes <xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> implementam um operador de conversão implícita para converter uma cadeia de caracteres em um <xref:System.Xml.Linq.XName> ou <xref:System.Xml.Linq.XNamespace>. Isso é como você obtém uma instância desses objetos. Você não pode obter uma instância usando um construtor, porque o construtor é inacessível.  
  
 <xref:System.Xml.Linq.XName> e <xref:System.Xml.Linq.XNamespace> também implementam os operadores de igualdade e desigualdade para determinar se dois objetos que estão sendo comparados são referências à mesma instância.  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria alguns objetos <xref:System.Xml.Linq.XElement> e demonstra que nomes idênticos compartilham a mesma instância.  
  
```csharp  
XElement r1 = new XElement("Root", "data1");  
XElement r2 = XElement.Parse("<Root>data2</Root>");  
  
if ((object)r1.Name == (object)r2.Name)  
    Console.WriteLine("r1 and r2 have names that refer to the same instance.");  
else  
    Console.WriteLine("Different");  
  
XName n = "Root";  
  
if ((object)n == (object)r1.Name)  
    Console.WriteLine("The name of r1 and the name in 'n' refer to the same instance.");  
else  
    Console.WriteLine("Different");  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
r1 and r2 have names that refer to the same instance.  
The name of r1 and the name in 'n' refer to the same instance.  
```  
  
 Como mencionado anteriormente, a vantagem de objetos atomizados é que quando você usa um dos métodos do eixo que recebem <xref:System.Xml.Linq.XName> como um parâmetro, o método do eixo só precisa determinar que dois nomes referenciam a mesma instância para selecionar os elementos desejados.  
  
 O exemplo a seguir passa um <xref:System.Xml.Linq.XName> para a chamada de método <xref:System.Xml.Linq.XContainer.Descendants%2A>, que terá um melhor desempenho devido ao padrão de atomização.  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("C1", 1),  
    new XElement("Z1",  
        new XElement("C1", 2),  
        new XElement("C1", 1)  
    )  
);  
  
var query = from e in root.Descendants("C1")  
            where (int)e == 1  
            select e;  
  
foreach (var z in query)  
    Console.WriteLine(z);  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<C1>1</C1>  
<C1>1</C1>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Desempenho (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)
