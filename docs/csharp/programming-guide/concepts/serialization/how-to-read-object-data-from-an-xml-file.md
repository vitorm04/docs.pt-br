---
title: Como ler dados de objeto de um arquivo XML (C#)
description: Este exemplo de C# lê dados de objeto que foram gravados anteriormente em um arquivo XML usando a classe XmlSerializer.
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 8d607424201cfad08df1c5ffbfb66a114b31886d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178756"
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="a4adb-103">Como ler dados de objeto de um arquivo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a4adb-103">How to read object data from an XML file (C#)</span></span>

<span data-ttu-id="a4adb-104">Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="a4adb-104">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4adb-105">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a4adb-105">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4adb-106">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="a4adb-106">Compiling the Code</span></span>  

<span data-ttu-id="a4adb-107">Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="a4adb-107">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="a4adb-108">Para obter mais informações sobre a serialização de dados, consulte [como gravar dados de objeto em um arquivo XML (C#)](./how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="a4adb-108">For more information about serializing data, see [How to write object data to an XML file (C#)](./how-to-write-object-data-to-an-xml-file.md).</span></span>
  
 <span data-ttu-id="a4adb-109">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a4adb-109">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="a4adb-110">Somente propriedades e campos públicos são desserializados.</span><span class="sxs-lookup"><span data-stu-id="a4adb-110">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a4adb-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="a4adb-111">Robust Programming</span></span>  

 <span data-ttu-id="a4adb-112">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="a4adb-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="a4adb-113">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="a4adb-113">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="a4adb-114">Os dados no arquivo não representam dados da classe a ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="a4adb-114">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="a4adb-115">O arquivo não existe (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="a4adb-115">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-security"></a><span data-ttu-id="a4adb-116">Segurança do .NET</span><span class="sxs-lookup"><span data-stu-id="a4adb-116">.NET Security</span></span>  

 <span data-ttu-id="a4adb-117">Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="a4adb-117">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="a4adb-118">O objeto recriado é executado em um computador local com as permissões do código que o desserializou.</span><span class="sxs-lookup"><span data-stu-id="a4adb-118">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="a4adb-119">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a4adb-119">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4adb-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="a4adb-120">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="a4adb-121">Como gravar dados de objeto em um arquivo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="a4adb-121">How to write object data to an XML file (C#)</span></span>](./how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="a4adb-122">Serialização (C#)</span><span class="sxs-lookup"><span data-stu-id="a4adb-122">Serialization (C#)</span></span>](./index.md)
- [<span data-ttu-id="a4adb-123">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="a4adb-123">C# Programming Guide</span></span>](../../index.md)
