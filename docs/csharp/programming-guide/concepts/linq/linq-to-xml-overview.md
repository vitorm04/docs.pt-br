---
title: "LINQ para vis&#227;o geral XML (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ para vis&#227;o geral XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

XML tem sido amplamente adotado como uma maneira de formatar dados em vários contextos. Por exemplo, você pode encontrar XML na Web, em arquivos de configuração, em arquivos do Microsoft Office Word e em bancos de dados.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é uma abordagem atualizada e redesenhada para a programação com XML. Ele fornece recursos de modificação do modelo de objeto de documento \(DOM\) de documento na memória e oferece suporte a [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] expressões de consulta. Embora essas expressões de consulta sejam sintaticamente diferentes de XPath, eles fornecem funcionalidade semelhante.  
  
## LINQ para desenvolvedores XML  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] tem como alvo uma variedade de desenvolvedores. Para um desenvolvedor médio que desejam realizar outras tarefas, apenas [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] facilita a XML, fornecendo uma experiência de consulta que é semelhante ao SQL. Com apenas um pouco de estudo, os programadores podem aprender a escrever consultas sucintas e eficientes na linguagem de programação de escolha.  
  
 Os desenvolvedores profissionais podem usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] para aumentar consideravelmente sua produtividade. Com [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], eles podem escrever menos código que é mais expressivo, mais compacto e mais eficientes. Eles podem usar as expressões de consulta de vários domínios de dados ao mesmo tempo.  
  
## O que é LINQ to XML?  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é uma habilitado para LINQ, de memória interface de programação XML que permite que você trabalhe com XML de dentro do [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] linguagens de programação.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é como modelo de objeto de documento \(DOM\) em que ele coloca o documento XML na memória. Você pode consultar e modificar o documento, e depois modificá\-lo você pode salvá\-lo em um arquivo ou serializá\-lo e enviá\-lo pela Internet. No entanto, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] difere do DOM: ele fornece um novo modelo de objeto que é mais leve e fácil de trabalhar, e que tira proveito dos recursos de linguagem no c\#.  
  
 A vantagem mais importante de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é sua integração com [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Essa integração permite que você escreva consultas no documento XML na memória para recuperar coleções de elementos e atributos. O recurso de consulta do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é comparável em funcionalidade \(embora não em sintaxe\) para XPath e XQuery. A integração do [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] em c\# fornece mais forte digitação, tempo de compilação Verificando e suporte a depurador aprimorado.  
  
 Outra vantagem do [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é a capacidade de usar os resultados da consulta como parâmetros para <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> construtores de objetos permite uma abordagem eficiente para criar árvores XML. Essa abordagem, chamada *construção funcional*, os desenvolvedores podem facilmente transformar árvores XML de uma forma para outra.  
  
 Por exemplo, você pode ter um XML típico ordem de compra, conforme descrito em [Sample XML File: Typical Purchase Order](../Topic/Sample%20XML%20File:%20Typical%20Purchase%20Order%20\(LINQ%20to%20XML\)3.md). Usando [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode executar a consulta a seguir para obter o valor de atributo de número de parte para cada elemento do item na ordem de compra:  
  
```c#  
IEnumerable<string> partNos =  
from item in purchaseOrder.Descendants("Item")  
select (string) item.Attribute("PartNumber");  
```  
  
 Como outro exemplo, você poderá obter uma lista, classificada pelo número de peça, dos itens com um valor maior que r $100. Para obter essas informações, você pode executar a consulta a seguir:  
  
```c#  
IEnumerable<XElement> partNos =  
from item in purchaseOrder.Descendants("Item")  
where (int) item.Element("Quantity") *  
    (decimal) item.Element("USPrice") > 100  
orderby (string)item.Element("PartNumber")  
select item;  
```  
  
 Além dessas [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)] recursos, [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fornece uma interface de programação XML aprimorada. Usando [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode:  
  
-   Carregar XML de arquivos ou fluxos.  
  
-   Serialize o XML em arquivos ou fluxos.  
  
-   Crie XML a partir do zero usando construção funcional.  
  
-   Consultar o XML usando eixos do tipo XPath.  
  
-   Manipular a árvore XML na memória usando métodos como <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A>, e <xref:System.Xml.Linq.XElement.SetValue%2A>.  
  
-   Valide árvores XML usando XSD.  
  
-   Use uma combinação desses recursos para transformar árvores XML de uma forma para outra.  
  
## Criando árvores XML  
 IOne das vantagens mais significativas da programação com [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é que é fácil criar árvores XML. Por exemplo, para criar uma árvore XML pequena, você pode escrever código da seguinte maneira:  
  
```c#  
XElement contacts =  
new XElement("Contacts",  
    new XElement("Contact",  
        new XElement("Name", "Patrick Hines"),  
        new XElement("Phone", "206-555-0144",   
            new XAttribute("Type", "Home")),  
        new XElement("phone", "425-555-0145",  
            new XAttribute("Type", "Work")),  
        new XElement("Address",  
            new XElement("Street1", "123 Main St"),  
            new XElement("City", "Mercer Island"),  
            new XElement("State", "WA"),  
            new XElement("Postal", "68042")  
        )  
    )  
);  
```  
  
 Para obter mais informações, consulte [Criando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## Consulte também  
 <xref:System.Xml.Linq>   
 [Guia de introdução \(LINQ to XML\)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)