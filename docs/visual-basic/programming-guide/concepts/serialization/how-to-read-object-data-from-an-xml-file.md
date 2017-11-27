---
title: 'Como: ler dados de objeto de um arquivo XML (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="38233-102">Como: ler dados de objeto de um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38233-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="38233-103">Este exemplo lê dados de objeto que foram previamente gravados em um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="38233-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38233-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38233-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="38233-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="38233-105">Compiling the Code</span></span>  
 <span data-ttu-id="38233-106">Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" pelo nome do arquivo que contém os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="38233-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="38233-107">Para obter mais informações sobre a serialização de dados, consulte [como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="38233-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="38233-108">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="38233-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="38233-109">Somente propriedades e campos públicos são desserializados.</span><span class="sxs-lookup"><span data-stu-id="38233-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="38233-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="38233-110">Robust Programming</span></span>  
 <span data-ttu-id="38233-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="38233-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="38233-112">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="38233-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="38233-113">Os dados no arquivo não representam dados da classe a ser desserializada.</span><span class="sxs-lookup"><span data-stu-id="38233-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="38233-114">O arquivo não existe (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="38233-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="38233-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38233-115">.NET Framework Security</span></span>  
 <span data-ttu-id="38233-116">Sempre verifique as entradas e nunca desserialize dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="38233-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="38233-117">O objeto recriado é executado em um computador local com as permissões do código que o desserializou.</span><span class="sxs-lookup"><span data-stu-id="38233-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="38233-118">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="38233-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38233-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38233-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="38233-120">Como gravar dados de objeto em um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38233-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="38233-121">Serialização (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38233-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="38233-122">Guia de programação do Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38233-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
