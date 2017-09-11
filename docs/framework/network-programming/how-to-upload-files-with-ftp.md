---
title: Como carregar arquivos com FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
caps.latest.revision: 5
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b90049c11e8eb1113155a400b7af159f2b6938ca
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-upload-files-with-ftp"></a><span data-ttu-id="f6c38-102">Como carregar arquivos com FTP</span><span class="sxs-lookup"><span data-stu-id="f6c38-102">How to: Upload Files with FTP</span></span>
<span data-ttu-id="f6c38-103">Este exemplo mostra como carregar um arquivo para um servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="f6c38-103">This sample shows how to upload a file to an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6c38-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f6c38-104">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");  
            request.Method = WebRequestMethods.Ftp.UploadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            // Copy the contents of the file to the request stream.  
            StreamReader sourceStream = new StreamReader("testfile.txt");  
            byte [] fileContents = Encoding.UTF8.GetBytes(sourceStream.ReadToEnd());  
            sourceStream.Close();  
            request.ContentLength = fileContents.Length;  
  
            Stream requestStream = request.GetRequestStream();  
            requestStream.Write(fileContents, 0, fileContents.Length);  
            requestStream.Close();  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Console.WriteLine("Upload File Complete, status {0}", response.StatusDescription);  
  
            response.Close();  
            }  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f6c38-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="f6c38-105">Compiling the Code</span></span>  
 <span data-ttu-id="f6c38-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="f6c38-106">This example requires:</span></span>  
  
-   <span data-ttu-id="f6c38-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="f6c38-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f6c38-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="f6c38-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="f6c38-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f6c38-109">.NET Framework Security</span></span>

