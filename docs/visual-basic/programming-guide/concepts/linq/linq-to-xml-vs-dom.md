---
title: LINQ to XML e DOM (Visual Basic) | Documentos do Microsoft
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
ms.assetid: 18c36130-d598-40b7-9007-828232252978
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 88b6bddcdeec2859844f5d5f94777146d488b5fb
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML e DOM (Visual Basic)
Esta seção descreve algumas das principais diferenças entre [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] e API, o modelo de objeto de documento (DOM) W3C de programação XML predominante atual.  
  
## <a name="new-ways-to-construct-xml-trees"></a>Novas maneiras de criar árvores XML  
 No W3C DOM, você cria uma árvore XML de baixo para cima; ou seja, você cria um documento, cria elementos e, em seguida, adiciona elementos ao documento.  
  
 Por exemplo, o seguinte seria uma maneira comum de criar uma árvore XML usando a implementação da Microsoft do DOM, <xref:System.Xml.XmlDocument>:</xref:System.Xml.XmlDocument>  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 Este estilo de codificação não fornece visualmente muitas informações sobre a estrutura da árvore XML. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]oferece suporte a essa abordagem para construir uma árvore XML, mas também oferece suporte a uma abordagem alternativa, *construção funcional*. No Visual Basic, a construção funcional usa literais XML para criar uma árvore XML.  
  
 Aqui está como você poderia construir a mesma árvore XML usando [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] construção funcional:  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Observe que o recuo do código para construir a árvore XML mostra a estrutura do XML subjacente.  
  
 Para obter mais informações, consulte [criar árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Trabalhando diretamente com Elementos XML  
 Quando você programa com XML, o foco principal é geralmente em elementos XML e talvez em atributos. No [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode trabalhar diretamente com elementos e atributos XML. Por exemplo, você pode fazer o seguinte:  
  
-   Criar elementos XML sem usar nenhum objeto de documento. Isso simplifica a programação quando você tem que trabalhar com partes de árvores XML.  
  
-   Carregue objetos `T:System.Xml.Linq.XElement` diretamente de um arquivo XML.  
  
-   Serialize objetos `T:System.Xml.Linq.XElement` para um arquivo ou fluxo.  
  
 Compare isso para o W3C DOM, no qual o documento XML é usado como um contêiner lógico para a árvore XML. No DOM, os nós XML, incluindo elementos e atributos, devem ser criados no contexto de um documento XML. Aqui está um fragmento de código para criar um elemento de nome DOM:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Se você quiser usar um elemento em vários documentos, deverá importar os nós nos documentos. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]evita essa camada de complexidade.  
  
 Ao usar LINQ to XML, você usa o <xref:System.Xml.Linq.XDocument>classe somente se você quiser adicionar uma instrução de processamento ou comentário no nível da raiz do documento.</xref:System.Xml.Linq.XDocument>  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Tratamento simplificado de nomes e namespaces  
 Tratar nomes, namespaces e prefixos de namespace é geralmente uma parte complexa da programação de XML. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]simplifica os nomes e namespaces eliminando a necessidade de lidar com prefixos de namespace. Se quiser, você pode controlar prefixos de namespace. Mas se você decidir não controlar explicitamente os prefixos de namespace [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] atribuirá prefixos de namespace durante a serialização se forem necessários, ou serializará usando namespaces padrão se não forem. Se namespaces padrão forem usados, haverá sem prefixos de namespace no documento resultante. Para obter mais informações, consulte [trabalhar com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Outro problema com os DOM é que ele não permite que você altere o nome de um nó. Em vez disso, você precisa criar um novo nó e copiar todos os nós filhos para ele, perdendo a identidade do nó original. [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]evita esse problema, permitindo que você defina o <xref:System.Xml.Linq.XName>propriedade em um nó.</xref:System.Xml.Linq.XName>  
  
## <a name="static-method-support-for-loading-xml"></a>Suporte de método estático para carregar XML  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]permite que você carregue XML usando métodos estáticos, em vez de métodos de instância. Isso simplifica o carregamento e a análise. Para obter mais informações, consulte [como: carregar XML de um arquivo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Remoção de suporte para construções de DTD  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]simplifica ainda mais a programação removendo o suporte para entidades e referências a entidades XML. O gerenciamento de entidades é complexo e raramente é utilizado. Remover o suporte aumenta o desempenho e simplifica a interface de programação. Quando um [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] árvore é preenchida, todas as entidades DTD são expandidas.  
  
## <a name="support-for-fragments"></a>Suporte para fragmentos  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]não fornece um equivalente para o `XmlDocumentFragment` classe. Em muitos casos, no entanto, o `XmlDocumentFragment` conceito pode ser tratado pelo resultado de uma consulta que é digitado como <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XNode>, ou <xref:System.Collections.Generic.IEnumerable%601>de <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Xml.Linq.XNode> </xref:System.Collections.Generic.IEnumerable%601>  
  
## <a name="support-for-xpathnavigator"></a>Suporte para XPathNavigator  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]fornece suporte para <xref:System.Xml.XPath.XPathNavigator>por meio de métodos de extensão no <xref:System.Xml.XPath?displayProperty=fullName>namespace.</xref:System.Xml.XPath?displayProperty=fullName> </xref:System.Xml.XPath.XPathNavigator> Para obter mais informações, consulte <xref:System.Xml.XPath.Extensions?displayProperty=fullName>.</xref:System.Xml.XPath.Extensions?displayProperty=fullName>  
  
## <a name="support-for-white-space-and-indentation"></a>Suporte para espaço em branco e recuo  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]manipula o espaço em branco mais simples que o DOM.  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados. Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Você pode não querer modificar este recuo de nenhuma forma. No [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode fazer isso preservando o espaço em branco ao carregar ou analisar o XML e desabilitando a formatação ao serializar o XML.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]armazena o espaço em branco como um <xref:System.Xml.Linq.XText>nó, em vez de ter especializado <xref:System.Xml.XmlNodeType>tipo de nó, como o DOM faz.</xref:System.Xml.XmlNodeType> </xref:System.Xml.Linq.XText>  
  
## <a name="support-for-annotations"></a>Suporte para anotações  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]elementos oferecem suporte a um conjunto extensível de anotações. Isso é útil para controlar informações variadas sobre um elemento, como informações de esquema, informações sobre se o elemento é associado a uma interface do usuário ou qualquer outra informação de tipo de aplicativo específico. Para obter mais informações, consulte [anotações LINQ to XML](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).  
  
## <a name="support-for-schema-information"></a>Suporte para informações do esquema  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]fornece suporte para validação de XSD por meio de métodos de extensão no <xref:System.Xml.Schema?displayProperty=fullName>namespace.</xref:System.Xml.Schema?displayProperty=fullName> Você pode validar que uma árvore XML está em conformidade com XSD. Você pode preencher a árvore XML com o PSVI (post-schema-validation infoset). Para obter mais informações, consulte [como: validar usando XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) e <xref:System.Xml.Schema.Extensions>.</xref:System.Xml.Schema.Extensions>  
  
## <a name="see-also"></a>Consulte também  
 [Introdução (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
