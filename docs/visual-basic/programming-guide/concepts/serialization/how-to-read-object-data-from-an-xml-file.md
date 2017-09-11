---
title: 'Como: ler dados de objeto de um arquivo XML (Visual Basic) | Documentos do Microsoft'
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3b9697f763a2d781c37960d46cbc7fa4536c84b4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="82d94-102">Como: ler dados de objeto de um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82d94-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="82d94-103">Este exemplo lê objeto dados que foram previamente gravados em um arquivo XML usando a <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="82d94-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82d94-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82d94-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="82d94-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="82d94-105">Compiling the Code</span></span>  
 <span data-ttu-id="82d94-106">Substitua o nome de arquivo "c:\temp\SerializationOverview.xml" com o nome do arquivo que contém os dados serializados.</span><span class="sxs-lookup"><span data-stu-id="82d94-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="82d94-107">Para obter mais informações sobre serialização de dados, consulte [como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="82d94-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="82d94-108">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="82d94-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="82d94-109">Apenas propriedades públicas e campos estão desserializados.</span><span class="sxs-lookup"><span data-stu-id="82d94-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="82d94-110">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="82d94-110">Robust Programming</span></span>  
 <span data-ttu-id="82d94-111">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="82d94-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="82d94-112">A classe sendo serializada não tem um construtor público, sem parâmetro.</span><span class="sxs-lookup"><span data-stu-id="82d94-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="82d94-113">Os dados no arquivo não representam dados da classe a ser desserializado.</span><span class="sxs-lookup"><span data-stu-id="82d94-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="82d94-114">O arquivo não existe (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="82d94-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="82d94-115">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="82d94-115">.NET Framework Security</span></span>  
 <span data-ttu-id="82d94-116">Sempre verifique se as entradas e nunca desserializar dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="82d94-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="82d94-117">O objeto recriado é executado em um computador local com as permissões do código que desserializado-lo.</span><span class="sxs-lookup"><span data-stu-id="82d94-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="82d94-118">Verifique todas as entradas antes de usar os dados no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="82d94-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82d94-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82d94-119">See Also</span></span>  
 <span data-ttu-id="82d94-120"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="82d94-120"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="82d94-121"> [Como: gravar dados de objeto para um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="82d94-121"> [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span></span>  
<span data-ttu-id="82d94-122"> [Serialização (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="82d94-122"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span></span>  
<span data-ttu-id="82d94-123"> [Guia de programação em Visual Basic](../../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="82d94-123"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md)</span></span>
