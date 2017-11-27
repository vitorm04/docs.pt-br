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
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 76b6006c34b29e17ea725a5f7d104c1b085b5edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="e3166-102">Como serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="e3166-102">How to: Serialize an Object</span></span>
<span data-ttu-id="e3166-103">Para serializar um objeto, primeiro crie o objeto a ser serializado e defina seus campos e propriedades públicos.</span><span class="sxs-lookup"><span data-stu-id="e3166-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="e3166-104">Para fazer isso, você deve determinar o formato de transporte em que o fluxo XML deve ser armazenado: como um fluxo ou como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3166-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="e3166-105">Por exemplo, se o fluxo XML precisar ser salvo de uma forma permanente, crie um objeto <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="e3166-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3166-106">Para obter mais exemplos de serialização XML, consulte [Exemplos de Serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="e3166-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="e3166-107">Para serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="e3166-107">To serialize an object</span></span>  
  
1.  <span data-ttu-id="e3166-108">Crie o objeto e defina seus campos e propriedades públicos.</span><span class="sxs-lookup"><span data-stu-id="e3166-108">Create the object and set its public fields and properties.</span></span>  
  
2.  <span data-ttu-id="e3166-109">Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="e3166-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="e3166-110">Para obter mais informações, consulte os construtores da classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e3166-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3.  <span data-ttu-id="e3166-111">Chame o método <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> para gerar um fluxo XML ou uma representação em arquivo de propriedades e campos públicos do objeto.</span><span class="sxs-lookup"><span data-stu-id="e3166-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="e3166-112">O exemplo a seguir cria um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3166-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e3166-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3166-113">See Also</span></span>  
 [<span data-ttu-id="e3166-114">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="e3166-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="e3166-115">Como desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="e3166-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
