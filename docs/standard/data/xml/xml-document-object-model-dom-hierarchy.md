---
title: Hierarquia DOM (Document Object Model) XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6dec61860fba5815b1dae802d280e8df6628ab91
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarquia DOM (Document Object Model) XML
A ilustração a seguir mostra a hierarquia de classes para o DOM (Document Object Model) XML, com o nome do World Wide Web Consortium (W3C) entre parênteses junto com o nome da classe onde é relevante.  
  
 ![Modelo de objeto de documento XML &#40; DOM &#41; hierarquia](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarquia DOM (Document Object Model) XML  
  
 As seguintes classes não herdam a **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 O **XmlImplementation** classe é usada para criar um documento XML. Para obter mais informações, consulte [criação de documentos XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 O **XmlNamedNodeMap** classe manipula um conjunto ordenado de nós. Para obter mais informações, consulte [recuperação não ordenada do nó por nome ou índice](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 O **XmlNodeList** classe manipula uma lista ordenada de nós. Para obter mais informações, consulte [recuperação de nó ordenada pelo índice](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 O **XmlNodeChangedEventArgs** classe manipula os manipuladores de eventos registrados no **XmlDocument**. Para obter mais informações, consulte [manipulação de eventos em um documento XML usando o XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 O **XmlLinkedNode** classe herda de **XmlNode**. Seu objetivo é substituir dois métodos de **XmlNode**: o **PreviousSibling** e **NextSibling** métodos. Esses métodos substituídos são então herdados e usados por **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, e **XmlProcessingInstruction**, que são classes que possuem irmão anterior e próximo.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
