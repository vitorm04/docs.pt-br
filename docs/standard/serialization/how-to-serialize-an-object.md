---
title: Como serializar um objeto
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: e988b7b56fca3f7e71c94155086bd242f8f9637b
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-serialize-an-object"></a>Como serializar um objeto
Para serializar um objeto, primeiro crie o objeto a ser serializado e defina seus campos e propriedades públicos. Para fazer isso, você deve determinar o formato de transporte em que o fluxo XML deve ser armazenado: como um fluxo ou como um arquivo. Por exemplo, se o fluxo XML precisar ser salvo de uma forma permanente, crie um objeto <xref:System.IO.FileStream>.  
  
> [!NOTE]
>  Para obter mais exemplos de serialização XML, consulte [Exemplos de Serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).  
  
### <a name="to-serialize-an-object"></a>Para serializar um objeto  
  
1.  Crie o objeto e defina seus campos e propriedades públicos.  
  
2.  Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto. Para obter mais informações, consulte os construtores da classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
3.  Chame o método <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> para gerar um fluxo XML ou uma representação em arquivo de propriedades e campos públicos do objeto. O exemplo a seguir cria um arquivo.  
  
    ```vb  
    Dim myObject As MySerializableClass = New MySerializableClass()  
    ' Insert code to set properties and fields of the object.  
    Dim mySerializer As XmlSerializer = New XmlSerializer(GetType(MySerializableClass))  
    ' To write to a file, create a StreamWriter object.  
    Dim myWriter As StreamWriter = New StreamWriter("myFileName.xml")  
    mySerializer.Serialize(myWriter, myObject)  
    myWriter.Close()  
    ```  
  
    ```csharp  
    MySerializableClass myObject = new MySerializableClass();  
    // Insert code to set properties and fields of the object.  
    XmlSerializer mySerializer = new   
    XmlSerializer(typeof(MySerializableClass));  
    // To write to a file, create a StreamWriter object.  
    StreamWriter myWriter = new StreamWriter("myFileName.xml");  
    mySerializer.Serialize(myWriter, myObject);  
    myWriter.Close();  
    ```  
  
## <a name="see-also"></a>Consulte também  
 [Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md)   
 [Como desserializar um objeto](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

