---
title: Como desserializar um objeto
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b28d80951cb2d71f8f8fb532710f738fecdf8508
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-deserialize-an-object"></a>Como desserializar um objeto
Quando você desserializar um objeto, o formato do transporte determina se você criará um fluxo ou objeto de arquivo. Após o formato do transporte ser determinado, você poderá chamar os métodos <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, conforme o necessário.  
  
### <a name="to-deserialize-an-object"></a>Para desserializar um objeto  
  
1.  Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto para desserializar.  
  
2.  Chame o método <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> para gerar uma réplica do objeto. Ao desserializar, você deverá converter o objeto retornado para o tipo do original, conforme mostrado no exemplo a seguir, o que desserializa o objeto em um arquivo (embora também possa ser desserializado em um fluxo).  
  
    ```vb  
    Dim myObject As MySerializableClass  
    ' Construct an instance of the XmlSerializer with the type  
    ' of object that is being deserialized.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To read the file, create a FileStream.  
    Dim myFileStream As FileStream = _  
    New FileStream("myFileName.xml", FileMode.Open)  
    ' Call the Deserialize method and cast to the object type.  
    myObject = CType( _  
    mySerializer.Deserialize(myFileStream), MySerializableClass)  
    ```  
  
    ```csharp  
    MySerializableClass myObject;  
    // Construct an instance of the XmlSerializer with the type  
    // of object that is being deserialized.  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(MySerializableClass));  
    // To read the file, create a FileStream.  
    FileStream myFileStream =   
    new FileStream("myFileName.xml", FileMode.Open);  
    // Call the Deserialize method and cast to the object type.  
    myObject = (MySerializableClass)   
    mySerializer.Deserialize(myFileStream)  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [Como serializar um objeto](../../../docs/standard/serialization/how-to-serialize-an-object.md)
