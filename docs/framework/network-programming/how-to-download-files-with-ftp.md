---
title: Como baixar arquivos com FTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 656a8de6a508d6834fd1866df14ec5378d4f84af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-download-files-with-ftp"></a><span data-ttu-id="9fbf2-102">Como baixar arquivos com FTP</span><span class="sxs-lookup"><span data-stu-id="9fbf2-102">How to: Download Files with FTP</span></span>
<span data-ttu-id="9fbf2-103">Este exemplo mostra como baixar um arquivo de um servidor FTP.</span><span class="sxs-lookup"><span data-stu-id="9fbf2-103">This sample shows how to download a file from an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fbf2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9fbf2-104">Example</span></span>  
  
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
            request.Method = WebRequestMethods.Ftp.DownloadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Download Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();    
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9fbf2-105">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="9fbf2-105">Compiling the Code</span></span>  
 <span data-ttu-id="9fbf2-106">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="9fbf2-106">This example requires:</span></span>  
  
-   <span data-ttu-id="9fbf2-107">Referências ao namespace **System.Net**.</span><span class="sxs-lookup"><span data-stu-id="9fbf2-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9fbf2-108">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="9fbf2-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9fbf2-109">Segurança do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9fbf2-109">.NET Framework Security</span></span>
