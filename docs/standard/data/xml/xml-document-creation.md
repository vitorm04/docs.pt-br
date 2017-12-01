---
title: "Criação de documentos XML"
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
ms.assetid: 877e9c62-b082-4bfb-bc5b-f47297eb30ef
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5a0806e34cfbf7c8e0b5ba995ca4876b8d10405e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-creation"></a>Criação de documentos XML
Existem duas maneiras de criar um documento XML. É uma maneira criar um **XmlDocument** sem parâmetros. A outra maneira é criar um **XmlDocument** e passá-lo um XmlNameTable como um parâmetro. O exemplo a seguir mostra como criar um novo e vazio **XmlDocument** usando sem parâmetros.  
  
```vb  
Dim doc As New XmlDocument()  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
```  
  
 Quando um documento é criado, você pode carregá-lo com dados de uma cadeia de caracteres, transmitir, URL, o leitor de texto, ou um **XmlReader** derivado da classe usando o **carregar** método. Também há outro método de carga, o **LoadXML** método, que lê o XML de uma cadeia de caracteres. Para obter mais informações sobre os vários **carga** métodos, consulte [ler um documento XML no DOM](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md).  
  
 Há uma classe chamada a **XmlNameTable**. Essa classe é uma tabela de objetos atomizados de cadeias de caracteres. Essa tabela fornece uma forma eficiente para que o analisador XML use o mesmo objeto de cadeia de caracteres para todos os nomes repetidos de elementos e de atributos em um documento XML. Um **XmlNameTable** é criado automaticamente quando um documento é criado como mostrado acima e é carregado com nomes de atributo e elemento quando o documento é carregado. Se você já tiver um documento com uma tabela de nome, e esses nomes pode ser útil em outro documento, você pode criar um novo documento usando o **carga** método que utiliza um **XmlNameTable** como um parâmetro. Quando o documento é criado com esse método, ele usa existente **XmlNameTable** todos os atributos e elementos já carregados do outro documento. Ela pode ser usada para comparar nomes de elementos e de atributos de forma mais eficaz. Para obter mais informações sobre o **XmlNameTable**, consulte [comparação de objeto usando XmlNameTable](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md). Para referência, consulte <xref:System.Xml.XmlNameTable>.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
