---
title: "LINQ to XML e DOM (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# LINQ to XML e DOM (C#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Esta seção descreve algumas das principais diferenças entre [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] e API, o modelo de objeto de documento \(DOM\) W3C de programação XML predominante atual.  
  
## Novas maneiras de criar árvores XML  
 O DOM do W3C, você cria uma árvore XML na parte inferior. ou seja, você cria um documento, criar elementos e, em seguida, adicione os elementos no documento.  
  
 Por exemplo, o seguinte seria uma maneira comum de criar uma árvore XML usando a implementação da Microsoft do DOM, <xref:System.Xml.XmlDocument>:  
  
```c#  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 Esse estilo de codificação não fornece visualmente muitas informações sobre a estrutura da árvore XML.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] oferece suporte a essa abordagem para construir uma árvore XML, mas também oferece suporte a uma abordagem alternativa, *construção funcional*. Construção funcional usa a <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XAttribute> construtores para criar uma árvore XML.  
  
 Aqui está como você poderia construir a mesma árvore XML usando [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] construção funcional:  
  
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
  
 Observe que o recuo do código para construir a árvore XML mostra a estrutura do XML subjacente.  
  
 Para obter mais informações, consulte [Criando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## Trabalhar diretamente com elementos XML  
 Quando você programa com XML, seu foco principal é geralmente em elementos XML e talvez em atributos. Em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode trabalhar diretamente com elementos e atributos XML. Por exemplo, você pode fazer o seguinte:  
  
-   Crie elementos XML sem usar um objeto de documento todo. Isso simplifica a programação quando você tem que trabalhar com fragmentos de árvores XML.  
  
-   Carga `T:System.Xml.Linq.XElement` objetos diretamente de um arquivo XML.  
  
-   Serializar `T:System.Xml.Linq.XElement` objetos em um arquivo ou um fluxo.  
  
 Compare isso com o DOM do W3C, em que o documento XML é usado como um contêiner lógico para a árvore XML. No DOM, nós XML, incluindo elementos e atributos, devem ser criados no contexto de um documento XML. Aqui está um fragmento de código para criar um elemento name no DOM:  
  
```c#  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Se você quiser usar um elemento em vários documentos, você deve importar os nós em todos os documentos.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] evita essa camada de complexidade.  
  
 Ao usar LINQ to XML, você usa o <xref:System.Xml.Linq.XDocument> classe somente se você quiser adicionar uma instrução de processamento ou comentário no nível da raiz do documento.  
  
## Tratamento simplificado de nomes e Namespaces  
 Tratamento de nomes, namespaces e prefixos de namespace é geralmente uma parte complexa da programação de XML.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] simplifica os nomes e namespaces eliminando a necessidade de lidar com prefixos de namespace. Se você quiser controlar prefixos de namespace, você pode. Mas se você decidir não controlar explicitamente os prefixos de namespace [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] atribuirá prefixos de namespace durante a serialização se forem necessários, ou serializará usando namespaces padrão se não forem. Se namespaces padrão forem usados, haverá sem prefixos de namespace no documento resultante. Para obter mais informações, consulte [Trabalhando com Namespaces XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Outro problema com o DOM é que ele não permite que você altere o nome de um nó. Em vez disso, você precisa criar um novo nó e copiar todos os nós filhos para ele, perdendo a identidade do nó original.[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] evita esse problema, permitindo que você defina o <xref:System.Xml.Linq.XName> propriedade em um nó.  
  
## Suporte de método estático para carregar o XML  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] permite que você carregue XML usando métodos estáticos, em vez de métodos de instância. Isso simplifica o carregamento e a análise. Para obter mais informações, consulte [Como: carregar XML de um arquivo \(c\#\)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## Remoção do suporte para construções de DTD  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] simplifica ainda mais a programação removendo o suporte para entidades e referências a entidades XML. O gerenciamento de entidades é complexo e raramente é utilizado. Remover o suporte aumenta o desempenho e simplifica a interface de programação. Quando um [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] árvore é preenchida, todas as entidades DTD são expandidas.  
  
## Suporte para fragmentos  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] não fornece um equivalente para o `XmlDocumentFragment` classe. Em muitos casos, no entanto, o `XmlDocumentFragment` conceito pode ser tratado pelo resultado de uma consulta que é digitado como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XNode>, ou <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>.  
  
## Suporte para XPathNavigator  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fornece suporte para <xref:System.Xml.XPath.XPathNavigator> por meio de métodos de extensão no <xref:System.Xml.XPath?displayProperty=fullName> namespace. Para obter mais informações, consulte <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.  
  
## Suporte para o espaço em branco e recuo  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] manipula o espaço em branco mais simples que o DOM.  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem quaisquer nós de texto de espaço em branco \(isto é, não preservar espaço em branco\), execute algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente significativo espaço em branco na árvore XML é preservado. Esse é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Não convém modificar este recuo de nenhuma forma. Em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode fazer isso por preservar espaço em branco quando você carregar ou analisar o XML e desabilitando a formatação ao serializar o XML.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] armazena o espaço em branco como um <xref:System.Xml.Linq.XText> nó, em vez de ter especializado <xref:System.Xml.XmlNodeType> tipo de nó, como o DOM faz.  
  
## Suporte para anotações  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] elementos oferecem suporte a um conjunto extensível de anotações. Isso é útil para controlar informações variadas sobre um elemento, como informações de esquema, informações sobre se o elemento é associado a uma interface do usuário ou qualquer outra informação de tipo de aplicativo específico. Para obter mais informações, consulte [LINQ to XML Annotations](../Topic/LINQ%20to%20XML%20Annotations1.md).  
  
## Suporte para informações de esquema  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fornece suporte para validação de XSD por meio de métodos de extensão no <xref:System.Xml.Schema?displayProperty=fullName> namespace. Você pode validar uma árvore XML está em conformidade com XSD. Você pode preencher a árvore XML com o post\-schema\-validation infoset \(PSVI\). Para obter mais informações, consulte [How to: Validate Using XSD](../Topic/How%20to:%20Validate%20Using%20XSD%20\(LINQ%20to%20XML\).md) e <xref:System.Xml.Schema.Extensions>.  
  
## Consulte também  
 [Guia de introdução \(LINQ to XML\)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)