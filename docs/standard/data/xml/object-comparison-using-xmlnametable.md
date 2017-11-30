---
title: "Comparação de objeto usando XmlNameTable"
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
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0cd1a3bad69499b4804299adecabad3a43b5eab1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="object-comparison-using-xmlnametable"></a>Comparação de objeto usando XmlNameTable
**XmlDocument**, quando criado, tem uma tabela de nome criada especificamente para esse documento. Quando o XML é carregado no documento ou novos elementos ou atributos são criados, os nomes de atributo e elemento são colocados no **XmlNameTable**. Você também pode criar um **XmlDocument** usando uma existente **NameTable** de outro documento. Quando **XmlDocument** são criados com o construtor que assume um **XmlNameTable** parâmetro, o documento tem acesso aos nomes de nó, namespaces e prefixos já armazenados na  **XmlNameTable**. Independentemente de como a tabela de nome é carregada com nomes, uma vez que os nomes são armazenados na tabela, os nomes podem ser comparados rapidamente usando a comparação de objeto em vez de comparação de cadeia de caracteres. Cadeias de caracteres também podem ser adicionadas para a tabela de nome usando o <xref:System.Xml.NameTable.Add%2A>. O exemplo de código a seguir mostra uma tabela de nome que está sendo criado e a cadeia de caracteres **MyString** que está sendo adicionado à tabela. Depois disso, um **XmlDocument** é criado usando essa tabela e os nomes de elemento e atributo no **Myfile.xml** são adicionadas à tabela de nome existente.  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 O exemplo de código a seguir mostra a criação de um documento, dois novos elementos que estão sendo adicionados ao documento, que também os adiciona à tabela do nome do documento, e a comparação de objeto em nomes.  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 A situação acima de uma tabela de nome transmitida entre dois documentos é típico quando o mesmo tipo de documento está sendo processado repetidamente, como documentos de ordem em um site de comércio eletrônico, que atendem a um esquema de linguagem de definição de esquema XML (XSD) ou Document type definition (DTD) e as mesmas cadeias de caracteres são repetidas. Usar a mesma tabela de nome fornece uma melhoria de desempenho, porque o mesmo nome de elemento ocorre em vários documentos.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
