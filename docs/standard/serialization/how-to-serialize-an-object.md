---
title: 'Como: serializar um objeto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.assetid: a1207d05-32b2-4953-8582-959607991227
ms.openlocfilehash: a587a132446a5f5d74b2d534b1ca3b93ccca1480
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928982"
---
# <a name="how-to-serialize-an-object"></a><span data-ttu-id="13ab2-102">Como: serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="13ab2-102">How to: Serialize an Object</span></span>
<span data-ttu-id="13ab2-103">Para serializar um objeto, primeiro crie o objeto a ser serializado e defina seus campos e propriedades públicos.</span><span class="sxs-lookup"><span data-stu-id="13ab2-103">To serialize an object, first create the object that is to be serialized and set its public properties and fields.</span></span> <span data-ttu-id="13ab2-104">Para fazer isso, você deve determinar o formato de transporte em que o fluxo XML deve ser armazenado: como um fluxo ou como um arquivo.</span><span class="sxs-lookup"><span data-stu-id="13ab2-104">To do this, you must determine the transport format in which the XML stream is to be stored, either as a stream or as a file.</span></span> <span data-ttu-id="13ab2-105">Por exemplo, se o fluxo XML precisar ser salvo de uma forma permanente, crie um objeto <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="13ab2-105">For example, if the XML stream must be saved in a permanent form, create a <xref:System.IO.FileStream> object.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="13ab2-106">Para obter mais exemplos de serialização XML, consulte [Exemplos de Serialização XML](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="13ab2-106">For more examples of XML serialization, see [Examples of XML Serialization](../../../docs/standard/serialization/examples-of-xml-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object"></a><span data-ttu-id="13ab2-107">Para serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="13ab2-107">To serialize an object</span></span>  
  
1. <span data-ttu-id="13ab2-108">Crie o objeto e defina seus campos e propriedades públicos.</span><span class="sxs-lookup"><span data-stu-id="13ab2-108">Create the object and set its public fields and properties.</span></span>  
  
2. <span data-ttu-id="13ab2-109">Construa um <xref:System.Xml.Serialization.XmlSerializer> usando o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="13ab2-109">Construct a <xref:System.Xml.Serialization.XmlSerializer> using the type of the object.</span></span> <span data-ttu-id="13ab2-110">Para obter mais informações, consulte os construtores da classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="13ab2-110">For more information, see the <xref:System.Xml.Serialization.XmlSerializer> class constructors.</span></span>  
  
3. <span data-ttu-id="13ab2-111">Chame o método <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> para gerar um fluxo XML ou uma representação em arquivo de propriedades e campos públicos do objeto.</span><span class="sxs-lookup"><span data-stu-id="13ab2-111">Call the <xref:System.Xml.Serialization.XmlSerializer.Serialize%2A> method to generate either an XML stream or a file representation of the object's public properties and fields.</span></span> <span data-ttu-id="13ab2-112">O exemplo a seguir cria um arquivo.</span><span class="sxs-lookup"><span data-stu-id="13ab2-112">The following example creates a file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="13ab2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13ab2-113">See also</span></span>

- [<span data-ttu-id="13ab2-114">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="13ab2-114">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="13ab2-115">Como: Desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="13ab2-115">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
