---
title: Como desserializar um objeto usando XmlSerializer
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deserializing objects
- objects, deserializing steps
ms.assetid: 287129c8-035a-4fea-b7b3-4790057ca076
ms.openlocfilehash: c24ba466a208fe5abdbf565169c41c4ee3f47482
ms.sourcegitcommit: f8c36054eab877de4d40a705aacafa2552ce70e9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/31/2019
ms.locfileid: "75559892"
---
# <a name="how-to-deserialize-an-object-using-xmlserializer"></a><span data-ttu-id="c181a-102">Como desserializar um objeto usando XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="c181a-102">How to deserialize an object using XmlSerializer</span></span>

<span data-ttu-id="c181a-103">Quando você desserializar um objeto, o formato do transporte determina se você criará um fluxo ou objeto de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c181a-103">When you deserialize an object, the transport format determines whether you will create a stream or file object.</span></span> <span data-ttu-id="c181a-104">Após o formato do transporte ser determinado, você poderá chamar os métodos <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> ou <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A>, conforme o necessário.</span><span class="sxs-lookup"><span data-stu-id="c181a-104">After the transport format is determined, you can call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> or <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> methods, as required.</span></span>

## <a name="to-deserialize-an-object"></a><span data-ttu-id="c181a-105">Para desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="c181a-105">To deserialize an object</span></span>

1. <span data-ttu-id="c181a-106">Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto para desserializar.</span><span class="sxs-lookup"><span data-stu-id="c181a-106">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object to deserialize.</span></span>

1. <span data-ttu-id="c181a-107">Chame o método <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> para gerar uma réplica do objeto.</span><span class="sxs-lookup"><span data-stu-id="c181a-107">Call the <xref:System.Xml.Serialization.XmlSerializer.Deserialize%2A> method to produce a replica of the object.</span></span> <span data-ttu-id="c181a-108">Ao desserializar, você deve converter o objeto retornado para o tipo do original, conforme mostrado no exemplo a seguir, que desserializa o objeto de um arquivo (embora ele também possa ser desserializado de um fluxo).</span><span class="sxs-lookup"><span data-stu-id="c181a-108">When deserializing, you must cast the returned object to the type of the original, as shown in the following example, which deserializes the object from a file (although it could also be deserialized from a stream).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c181a-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="c181a-109">See also</span></span>

- [<span data-ttu-id="c181a-110">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="c181a-110">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="c181a-111">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="c181a-111">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
