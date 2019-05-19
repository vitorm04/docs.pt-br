---
title: 'Como: desserializar um objeto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e1a960d39319beee1c3c257fcd3ade207de11010
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881135"
---
# <a name="how-to-deserialize-an-object"></a><span data-ttu-id="b73f5-102">Como: desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b73f5-102">How to: Deserialize an Object</span></span>
<span data-ttu-id="b73f5-103">Quando você desserializar um objeto, o formato do transporte determina se você criará um fluxo ou objeto de arquivo.</span><span class="sxs-lookup"><span data-stu-id="b73f5-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="b73f5-104">Após o formato do transporte ser determinado, você poderá chamar os métodos <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="b73f5-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="b73f5-105">Para desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b73f5-105">To deserialize an object</span></span>  
  
1. <span data-ttu-id="b73f5-106">Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto para desserializar.</span><span class="sxs-lookup"><span data-stu-id="b73f5-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>  
  
2. <span data-ttu-id="b73f5-107">Chame o método <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> para gerar uma réplica do objeto.</span><span class="sxs-lookup"><span data-stu-id="b73f5-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="b73f5-108">Ao desserializar, você deve converter o objeto retornado para o tipo do original, conforme mostrado no exemplo a seguir, que desserializa o objeto de um arquivo (embora também possa ser desserializado de um fluxo).</span><span class="sxs-lookup"><span data-stu-id="b73f5-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b73f5-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b73f5-109">See also</span></span>

- [<span data-ttu-id="b73f5-110">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="b73f5-110">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="b73f5-111">Como: Serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b73f5-111">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
