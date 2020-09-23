---
title: Como ler dados de objeto a partir de um arquivo XML
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: 7677b32f76bee3fe579f96715b6c748c08c83a82
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077235"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="18117-102">Como ler dados de objeto de um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18117-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>

<span data-ttu-id="18117-103">Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="18117-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18117-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18117-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compile-the-code"></a><span data-ttu-id="18117-105">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="18117-105">Compile the code</span></span>  

 <span data-ttu-id="18117-106">Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="18117-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="18117-107">Para obter mais informações sobre a serialização de dados, consulte [como: gravar dados de objeto em um arquivo XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="18117-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="18117-108">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18117-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="18117-109">Somente propriedades e campos públicos são desserializados.</span><span class="sxs-lookup"><span data-stu-id="18117-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="18117-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="18117-110">Robust Programming</span></span>  

 <span data-ttu-id="18117-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="18117-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="18117-112">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="18117-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="18117-113">Os dados no arquivo não representam dados da classe a ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="18117-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="18117-114">O arquivo não existe (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="18117-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="18117-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="18117-115">.NET Framework Security</span></span>  

 <span data-ttu-id="18117-116">Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="18117-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="18117-117">O objeto recriado é executado em um computador local com as permissões do código que o desserializou.</span><span class="sxs-lookup"><span data-stu-id="18117-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="18117-118">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="18117-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18117-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="18117-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="18117-120">Como gravar dados de objeto em um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18117-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="18117-121">Serialização (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18117-121">Serialization (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="18117-122">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18117-122">Visual Basic Programming Guide</span></span>](../../index.md)
