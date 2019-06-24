---
title: Visão geral do LINQ to XML (C#)
ms.date: 10/30/2018
ms.assetid: 716b94d3-0091-4de1-8e05-41bc069fa9dd
ms.openlocfilehash: 6a7d681b52bbc6ce515e2202f3f448ce4ba79ced
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267953"
---
# <a name="linq-to-xml-overview-c"></a>Visão geral do LINQ to XML (C#)

O LINQ to XML fornece uma interface de programação XML na memória que aproveita a .NET LINQ (Consulta Integrada à Linguagem) Framework. O LINQ to XML usa os recursos do .NET e pode ser comparado a uma interface de programação XML de Modelo de Objeto do Documento (DOM) atualizada e reprojetada. 
 
O XML tem sido amplamente adotado como um modo de formatar dados em muitos contextos. Por exemplo, você pode encontrar XML na Web, em arquivos de configuração, em arquivos do Microsoft Office Word e em bancos de dados.

O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma abordagem atualizada e redesenhada para a programação com XML. Ele oferece os recursos de modificação de documentos na memória do DOM (Document Object Model), bem como o suporte a expressões de consulta [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]. Embora essas expressões de consulta sejam sintaticamente diferentes de XPath, elas oferecem uma funcionalidade semelhante.

## <a name="linq-to-xml-developers"></a>Desenvolvedores em LINQ to XML

O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] se destina a uma variedade de desenvolvedores. Para um desenvolvedor médio que deseja apenas ter algo concluído, o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] torna o XML mais simples ao oferecer uma experiência de consulta que é semelhante ao SQL. Com apenas um pouco de estudo, os programadores podem aprender a escrever consultas sucintas e eficientes na linguagem de programação de sua escolha.

Os desenvolvedores profissionais podem usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para aumentar consideravelmente sua produtividade. Com o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], eles podem escrever um código menor que seja mais expressivo, mais compacto e mais eficiente. Eles podem usar expressões de consulta de vários domínios de dados ao mesmo tempo.

## <a name="what-is-linq-to-xml"></a>O que é o LINQ to XML?

O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é uma interface de programação XML na memória e habilitada para LINQ que permite que você trabalhe com XML de dentro das linguagens de programação do .NET Framework.

O [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é como o DOM (Modelo de Objeto do Documento) no sentido de levar o documento XML para a memória. Você pode consultar e modificar o documento e, depois de modificá-lo, pode salvá-lo em um arquivo ou serializá-lo e enviá-lo pela Internet. No entanto, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é diferente do DOM: Ele fornece um novo modelo de objeto mais leve e mais fácil de se trabalhar e que aproveita as funcionalidades de linguagem em C#.

A vantagem mais importante do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é sua integração com o [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Essa integração permite que você escreva consultas no documento XML na memória para recuperar coleções de elementos e atributos. O recurso de consulta do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é comparável em funcionalidade (embora não em sintaxe) a XPath e XQuery. A integração de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] no C# oferece tipagem mais forte, verificação em tempo de compilação e melhor suporte de depuração.

Outra vantagem do [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é a capacidade de usar resultados da consulta como parâmetros para construtores de objeto <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute>, o que permite uma abordagem eficiente para a criação de árvores XML. Essa abordagem, chamada de *construção funcional*, permite que os desenvolvedores transformem com facilidade árvores XML de uma forma em outra.

Por exemplo, você pode ter uma ordem de compra XML típica, conforme descrito em [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](sample-xml-file-typical-purchase-order-linq-to-xml-1.md). Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você poderia executar a consulta a seguir para obter o valor do atributo de número de peça para cada elemento de item na ordem de compra:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<string> partNos =  from item in purchaseOrder.Descendants("Item")
                               select (string) item.Attribute("PartNumber");
```

Isso pode ser regravado no formulário de sintaxe do método:

```csharp
IEnumerable<string> partNos = purchaseOrder.Descendants("Item").Select(x => (string) x.Attribute("PartNumber"));
```

Como outro exemplo, você poderia querer uma lista, classificada por número de peça, dos itens com um valor maior que $ 100. Para obter essas informações, você poderia executar a seguinte consulta:

```csharp
// Load the XML file from our project directory containing the purchase orders
var filename = "PurchaseOrder.xml";
var currentDirectory = Directory.GetCurrentDirectory();
var purchaseOrderFilepath = Path.Combine(currentDirectory, filename);

XElement purchaseOrder = XElement.Load($"{purchaseOrderFilepath}");

IEnumerable<XElement> pricesByPartNos =  from item in purchaseOrder.Descendants("Item")
                                 where (int) item.Element("Quantity") * (decimal) item.Element("USPrice") > 100
                                 orderby (string)item.Element("PartNumber")
                                 select item;
```

Outra vez, isso pode ser regravado no formulário de sintaxe do método:

```csharp
IEnumerable<XElement> pricesByPartNos = purchaseOrder.Descendants("Item")
                                        .Where(item => (int)item.Element("Quantity") * (decimal)item.Element("USPrice") > 100)
                                        .OrderBy(order => order.Element("PartNumber"));
```

Além desses recursos de [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)], o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oferece uma interface de programação XML aprimorada. Usando o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode:

- Carregar XML de [arquivos](how-to-load-xml-from-a-file.md) ou [fluxos](how-to-stream-xml-fragments-from-an-xmlreader.md).

- Serializar o XML em arquivos ou fluxos.

- Crie XML a partir do zero usando a construção funcional.

- Consultar o XML usando eixos do tipo XPath.

- Manipular a árvore XML na memória usando métodos como <xref:System.Xml.Linq.XContainer.Add%2A>, <xref:System.Xml.Linq.XNode.Remove%2A>, <xref:System.Xml.Linq.XNode.ReplaceWith%2A> e <xref:System.Xml.Linq.XElement.SetValue%2A>.

- Validar árvores XML usando XSD.

- Usar uma combinação desses recursos para transformar árvores XML de uma forma em outra.

## <a name="creating-xml-trees"></a>Criando árvores XML

Uma das vantagens mais significativas da programação com [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] é que é fácil criar árvores XML. Por exemplo, para criar uma árvore XML pequena, você pode escrever código da seguinte forma:

```csharp
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

Para obter mais informações, consulte [Criando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).

## <a name="see-also"></a>Consulte também

- [Referência (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/reference-linq-to-xml.md)
- [LINQ to XML versus DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md)
- [LINQ to XML versus Outras Tecnologias XML](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-other-xml-technologies.md)
- <xref:System.Xml.Linq>
