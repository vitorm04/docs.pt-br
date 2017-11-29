---
title: Como carregar arquivos com FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 08002bf223d96d49cffb67ec744659747fa49e26
ms.sourcegitcommit: 32f5e1db8755ed7dfac0b4ec764fa809e5a7548c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2017
---
# <a name="how-to-upload-files-with-ftp"></a><span data-ttu-id="04543-102">Como carregar arquivos com FTP</span><span class="sxs-lookup"><span data-stu-id="04543-102">How to: Upload Files with FTP</span></span>
<span data-ttu-id="04543-103">Este exemplo mostra como carregar um arquivo para um servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="04543-103">This sample shows how to upload a file to an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04543-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="04543-104">Example</span></span>  
  
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
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="04543-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="04543-105">Compiling the Code</span></span>  
 <span data-ttu-id="04543-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="04543-106">This example requires:</span></span>  
  
-   <span data-ttu-id="04543-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="04543-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="04543-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="04543-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="04543-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="04543-109">.NET Framework Security</span></span>
