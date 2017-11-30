---
title: Criando novos atributos para elementos no DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a>Criando novos atributos para elementos no DOM
Criar novos atributos é diferente de criar outros tipos de nó, porque os atributos não são nós, mas são propriedades de um nó de elemento e estão contidos em um **XmlAttributeCollection** associada ao elemento. Há várias maneiras de criar um atributo e anexá-lo a um elemento:  
  
-   Obter o nó de elemento e use **SetAttribute** para adicionar um atributo à coleção de atributos desse elemento.  
  
-   Criar um **XmlAttribute** nó usando o **CreateAttribute** método, obter o nó de elemento, em seguida, usar **SetAttributeNode** para adicionar o nó para a coleção de atributos que elemento.  
  
 O exemplo a seguir mostra como adicionar um atributo a um elemento usando o **SetAttribute** método.  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 O exemplo a seguir mostra um novo atributo que está sendo criado usando o **CreateAttribute** método. Mostra o atributo adicionado à coleção de atributos, em seguida, o **catálogo** elemento usando o **SetAttributeNode** método.  
  
 Com o seguinte XML:  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 crie um novo atributo e atribua um valor a ele:  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 e anexe-o ao elemento:  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 **Saída**  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 O exemplo de código completo pode ser encontrado em <xref:System.Xml.XmlDocument.CreateAttribute%2A>.  
  
 Você também pode criar um **XmlAttribute** nó e use o **InsertBefore** ou **InsertAfter** métodos para colocá-lo na posição apropriada na coleção. Se um atributo com o mesmo nome já está presente na coleção de atributos, existente **XmlAttribute** nó for removido da coleção e o novo **XmlAttribute** nó é inserido. Isso executa da mesma forma que o **SetAttribute** método. Esses métodos tomar, como um parâmetro, um nó existente como um ponto de referência para fazer o **InsertBefore** e **InsertAfter**. Se você não fornecer um nó de referência que indica onde inserir o novo nó, o padrão para o **InsertAfter** método é inserir o novo nó no início da coleção. A posição padrão para o **InsertBefore**, se nenhum nó de referência for fornecido, o final da coleção.  
  
 Se você tiver criado um **XmlNamedNodeMap** de atributos, você pode adicionar um atributo por nome usando o <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>. Para obter mais informações, consulte [coleções de nó em NamedNodeMaps e em NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).  
  
## <a name="default-attributes"></a>Atributos padrão  
 Se você criar um elemento que está declarado para ter um atributo padrão, um novo atributo padrão com seu valor padrão será criado pelo DOM (Document Object Model) XML e anexado ao elemento. Os nós filhos do atributo padrão também são criados neste momento.  
  
## <a name="attribute-child-nodes"></a>Nós filhos do atributo  
 O valor de um nó de atributo se torna os seus nós filhos. Há apenas dois tipos de nós filho válido: **XmlText** nós, e **XmlEntityReference** nós. Esses são nós filho no sentido de que os métodos como **FirstChild** e **LastChild** processá-los como nós filho. Essa distinção de um atributo que possui nós filhos é importante ao tentar remover atributos ou nós filhos do atributo. Para obter mais informações, consulte [remover atributos de um nó de elemento no DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
