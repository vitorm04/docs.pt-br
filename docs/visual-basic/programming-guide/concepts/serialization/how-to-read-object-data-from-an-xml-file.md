---
title: 'Como: ler dados de objeto de um arquivo XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: fa8623abeebfa413677b4b68d6ab6b7a0547ccd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646052"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="9d0bd-102">Como: ler dados de objeto de um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d0bd-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="9d0bd-103">Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d0bd-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9d0bd-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d0bd-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9d0bd-105">Compiling the Code</span></span>  
 <span data-ttu-id="9d0bd-106">Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="9d0bd-107">Para obter mais informações sobre a serialização de dados, consulte [como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="9d0bd-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="9d0bd-108">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="9d0bd-109">Somente propriedades e campos públicos são desserializados.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9d0bd-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9d0bd-110">Robust Programming</span></span>  
 <span data-ttu-id="9d0bd-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="9d0bd-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9d0bd-112">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="9d0bd-113">Os dados no arquivo não representam dados da classe a ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="9d0bd-114">O arquivo não existe (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9d0bd-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9d0bd-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9d0bd-115">.NET Framework Security</span></span>  
 <span data-ttu-id="9d0bd-116">Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="9d0bd-117">O objeto recriado é executado em um computador local com as permissões do código que o desserializou.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="9d0bd-118">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d0bd-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0bd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9d0bd-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="9d0bd-120">Como gravar dados de objeto em um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d0bd-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="9d0bd-121">Serialização (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d0bd-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="9d0bd-122">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d0bd-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
