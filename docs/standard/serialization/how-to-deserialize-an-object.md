---
title: Como desserializar um objeto usando XmlSerializer
description: Saiba como desserializar um objeto. O formato de transporte determina se um objeto de fluxo ou de arquivo deve ser criado.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: e08ae0d77539219223650fd3bcbd1bcee4df2739
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379110"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="b886d-104">Como desserializar um objeto usando XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="b886d-104">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="b886d-105">Quando você desserializar um objeto, o formato do transporte determina se você criará um fluxo ou objeto de arquivo.</span><span class="sxs-lookup"><span data-stu-id="b886d-105">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="b886d-106">Após o formato do transporte ser determinado, você poderá chamar os métodos <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="b886d-106">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="b886d-107">Para desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b886d-107">To deserialize an object</span></span>

1. <span data-ttu-id="b886d-108">Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto para desserializar.</span><span class="sxs-lookup"><span data-stu-id="b886d-108">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="b886d-109">Chame o método <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> para gerar uma réplica do objeto.</span><span class="sxs-lookup"><span data-stu-id="b886d-109">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="b886d-110">Ao desserializar, você deve converter o objeto retornado para o tipo do original, conforme mostrado no exemplo a seguir, que desserializa o objeto de um arquivo (embora ele também possa ser desserializado de um fluxo).</span><span class="sxs-lookup"><span data-stu-id="b886d-110">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

    ```vb
    ' Construct an instance of the XmlSerializer with the type
    ' of object that is being deserialized.
    Dim mySerializer As New XmlSerializer(GetType(MySerializableClass))
    ' To read the file, create a FileStream.
    Dim myFileStream As New FileStream("myFileName.xml", FileMode.Open)
    ' Call the Deserialize method and cast to the object type.
    Dim myObject = CType( _
    mySerializer.Deserialize(myFileStream), MySerializableClass)
    ```

    ```csharp
    // Construct an instance of the XmlSerializer with the type
    // of object that is being deserialized.
    var mySerializer = new XmlSerializer(typeof(MySerializableClass));
    // To read the file, create a FileStream.
    var myFileStream = new FileStream("myFileName.xml", FileMode.Open);
    // Call the Deserialize method and cast to the object type.
    var myObject = (MySerializableClass) mySerializer.Deserialize(myFileStream)
    ```

## <a name="see-also"></a><span data-ttu-id="b886d-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="b886d-111">See also</span></span>

- [<span data-ttu-id="b886d-112">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="b886d-112">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="b886d-113">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="b886d-113">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
