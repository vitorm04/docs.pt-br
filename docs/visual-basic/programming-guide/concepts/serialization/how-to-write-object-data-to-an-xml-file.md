---
title: 'Como: Gravar dados de objeto para um arquivo XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 17f8463a4b905028d37a2e005562867f87f4bd2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624362"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="e3e49-102">Como: Gravar dados de objeto para um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3e49-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="e3e49-103">Este exemplo grava o objeto de uma classe para um arquivo XML usando a classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e3e49-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3e49-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3e49-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3e49-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e3e49-105">Compiling the Code</span></span>  
 <span data-ttu-id="e3e49-106">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e3e49-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e3e49-107">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e3e49-107">Robust Programming</span></span>  
 <span data-ttu-id="e3e49-108">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="e3e49-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="e3e49-109">A classe que está sendo serializada não tem um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e3e49-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="e3e49-110">O arquivo existe e é somente leitura (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e3e49-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="e3e49-111">O caminho é muito longo (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="e3e49-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="e3e49-112">O disco está cheio (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e3e49-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e3e49-113">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e3e49-113">.NET Framework Security</span></span>  
 <span data-ttu-id="e3e49-114">Este exemplo cria um novo arquivo, se o arquivo ainda não existe.</span><span class="sxs-lookup"><span data-stu-id="e3e49-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="e3e49-115">Se um aplicativo precisar criar um arquivo, ele precisará de acesso `Create` para a pasta.</span><span class="sxs-lookup"><span data-stu-id="e3e49-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="e3e49-116">Se o arquivo já existe, o aplicativo precisa apenas de acesso `Write`, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="e3e49-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="e3e49-117">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder acesso `Read` a um único arquivo, em vez de acesso `Create` a uma pasta.</span><span class="sxs-lookup"><span data-stu-id="e3e49-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3e49-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3e49-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="e3e49-119">Como: Ler dados de objeto de um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3e49-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="e3e49-120">Serialização (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3e49-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
