---
title: Como ler dados de objeto de um arquivo XML (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 02ff7a209cd78c70c6e3c443105d27b33c6f0af4
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="b1cb8-102">Como ler dados de objeto de um arquivo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="b1cb8-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="b1cb8-103">Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1cb8-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1cb8-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="b1cb8-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="b1cb8-105">Compiling the Code</span></span>  
 <span data-ttu-id="b1cb8-106">Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="b1cb8-107">Para obter mais informações sobre a serialização de dados, consulte [Como gravar dados de objeto em um arquivo XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="b1cb8-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="b1cb8-108">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="b1cb8-109">Somente propriedades e campos públicos são desserializados.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b1cb8-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="b1cb8-110">Robust Programming</span></span>  
 <span data-ttu-id="b1cb8-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="b1cb8-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="b1cb8-112">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="b1cb8-113">Os dados no arquivo não representam dados da classe a ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="b1cb8-114">O arquivo não existe (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="b1cb8-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b1cb8-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1cb8-115">.NET Framework Security</span></span>  
 <span data-ttu-id="b1cb8-116">Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="b1cb8-117">O objeto recriado é executado em um computador local com as permissões do código que o desserializou.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="b1cb8-118">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b1cb8-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1cb8-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1cb8-119">See Also</span></span>  
 <span data-ttu-id="b1cb8-120"><xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="b1cb8-120"><xref:System.IO.StreamWriter></span></span>   
 <span data-ttu-id="b1cb8-121">[Como gravar dados de objeto em um arquivo XML (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="b1cb8-121">[How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span></span>  
 <span data-ttu-id="b1cb8-122">[Serialização (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="b1cb8-122">[Serialization (C# )](../../../../csharp/programming-guide/concepts/serialization/index.md) </span></span>  
 [<span data-ttu-id="b1cb8-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b1cb8-123">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)

