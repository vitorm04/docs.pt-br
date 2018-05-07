---
title: Como desserializar um objeto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: 957c332b3456e2b27aca36ef2bcabbc36b4e94e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
