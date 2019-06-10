---
title: 'Como: Localizar um elemento com um elemento filho específico (C#)'
ms.date: 07/20/2015
ms.assetid: 00cf5555-374e-4369-bf93-7bd2e7f21db3
ms.openlocfilehash: 71068774b93581fdd82a0fe57651bc7780ca1ef1
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485578"
---
# <a name="how-to-find-an-element-with-a-specific-child-element-c"></a>Como: Localizar um elemento com um elemento filho específico (C#)
Este tópico mostra como localizar determinado elemento que tem um elemento filho com um valor específico.  
  
## <a name="example"></a>Exemplo  
 O exemplo localiza o elemento `Test` que possui um elemento filho `CommandLine` com o valor "Examp2.EXE".  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Configuração de teste (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("TestConfig.xml");  
IEnumerable<XElement> tests =  
    from el in root.Elements("Test")  
    where (string)el.Element("CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Esse código gera a seguinte saída:  
  
```  
0002  
0006  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra a mesma consulta para XML que está em um namespace. Para obter mais informações, consulte [Trabalhando com namespaces XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Configuração de teste em um namespace](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-test-configuration-in-a-namespace1.md).  
  
```csharp  
XElement root = XElement.Load("TestConfigInNamespace.xml");  
XNamespace ad = "http://www.adatum.com";  
IEnumerable<XElement> tests =  
    from el in root.Elements(ad + "Test")  
    where (string)el.Element(ad + "CommandLine") == "Examp2.EXE"  
    select el;  
foreach (XElement el in tests)  
    Console.WriteLine((string)el.Attribute("TestId"));  
```  
  
 Esse código gera a seguinte saída:  
  
```  
0002  
0006  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XElement.Attribute%2A>
- <xref:System.Xml.Linq.XContainer.Elements%2A>
- [Visão geral de operadores de consulta padrão (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [Operações de projeção (C#)](../../../../csharp/programming-guide/concepts/linq/projection-operations.md)
