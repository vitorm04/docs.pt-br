---
title: 'Como: gravar dados de objeto para um arquivo XML (Visual Basic) | Documentos do Microsoft'
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
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
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
ms.openlocfilehash: 27131f357c1f5afc75645bff88ae5d7cd2395617
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="fea04-102">Como: gravar dados de objeto para um arquivo XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fea04-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="fea04-103">Teste de exemplo grava o objeto de uma classe para um arquivo XML usando a <xref:System.Xml.Serialization.XmlSerializer>classe.</xref:System.Xml.Serialization.XmlSerializer></span><span class="sxs-lookup"><span data-stu-id="fea04-103">TThis example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fea04-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fea04-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="fea04-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fea04-105">Compiling the Code</span></span>  
 <span data-ttu-id="fea04-106">A classe deve ter um construtor público sem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fea04-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fea04-107">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="fea04-107">Robust Programming</span></span>  
 <span data-ttu-id="fea04-108">As seguintes condições podem causar uma exceção:</span><span class="sxs-lookup"><span data-stu-id="fea04-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="fea04-109">A classe sendo serializada não tem um construtor público, sem parâmetro.</span><span class="sxs-lookup"><span data-stu-id="fea04-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="fea04-110">O arquivo existe e é somente leitura (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="fea04-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fea04-111">O caminho é muito longo (<xref:System.IO.PathTooLongException>).</xref:System.IO.PathTooLongException></span><span class="sxs-lookup"><span data-stu-id="fea04-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="fea04-112">O disco está cheio (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="fea04-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fea04-113">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fea04-113">.NET Framework Security</span></span>  
 <span data-ttu-id="fea04-114">Este exemplo cria um novo arquivo, se o arquivo ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="fea04-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="fea04-115">Se um aplicativo precisar criar um arquivo, o aplicativo precisa `Create` acesso para a pasta.</span><span class="sxs-lookup"><span data-stu-id="fea04-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="fea04-116">Se o arquivo já existir, o aplicativo precisa apenas `Write` acessar, um privilégio menor.</span><span class="sxs-lookup"><span data-stu-id="fea04-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="fea04-117">Sempre que possível, é mais seguro criar o arquivo durante a implantação e somente conceder `Read` acesso a um único arquivo, em vez de `Create` acesso para uma pasta.</span><span class="sxs-lookup"><span data-stu-id="fea04-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea04-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fea04-118">See Also</span></span>  
 <span data-ttu-id="fea04-119"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="fea04-119"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="fea04-120"> [Como: ler dados de objeto de um arquivo XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="fea04-120"> [How to: Read Object Data from an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span></span>  
<span data-ttu-id="fea04-121"> [Serialização (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span><span class="sxs-lookup"><span data-stu-id="fea04-121"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span></span>
