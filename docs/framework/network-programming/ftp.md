---
title: FTP
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
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
caps.latest.revision: 9
author: mcleblanc
ms.author: markl
manager: markl
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d2274873140c415a970884389e71163be7f4cba6
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="ftp"></a><span data-ttu-id="c9cbb-102">FTP</span><span class="sxs-lookup"><span data-stu-id="c9cbb-102">FTP</span></span>
<span data-ttu-id="c9cbb-103">O .NET Framework fornece suporte abrangente para o protocolo FTP com as classes <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="c9cbb-103">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="c9cbb-104">Essas classes são derivadas de <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="c9cbb-104">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="c9cbb-105">Na maioria dos casos, as classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> fornecem tudo o que é necessário para fazer a solicitação, mas se você precisar acessar os recursos específicos ao FTP expostos como propriedades, poderá fazer a conversão de tipo dessas classes em <xref:System.Net.FtpWebRequest> ou <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="c9cbb-105">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c9cbb-106">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c9cbb-106">Examples</span></span>  
 <span data-ttu-id="c9cbb-107">Para obter mais informações, consulte os seguintes tópicos: [Como baixar arquivos com FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [Como carregar arquivos com FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md) e [Como listar o conteúdo do diretório com FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="c9cbb-107">For more information, see the following topics: [How to: Download Files with FTP](../../../docs/framework/network-programming/how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](../../../docs/framework/network-programming/how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](../../../docs/framework/network-programming/how-to-list-directory-contents-with-ftp.md).</span></span>  
  
## <a name="ftp-and-proxies"></a><span data-ttu-id="c9cbb-108">FTP e proxies</span><span class="sxs-lookup"><span data-stu-id="c9cbb-108">FTP and proxies</span></span>  
 <span data-ttu-id="c9cbb-109">Se um proxy (especificado pela propriedade <xref:System.Net.FtpWebRequest.Proxy%2A>) for um proxy HTTP, haverá suporte apenas para os comandos <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> e <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails>.</span><span class="sxs-lookup"><span data-stu-id="c9cbb-109">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9cbb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9cbb-110">See Also</span></span>  
 <span data-ttu-id="c9cbb-111">[Acessando a Internet por meio de um proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md) </span><span class="sxs-lookup"><span data-stu-id="c9cbb-111">[Accessing the Internet Through a Proxy](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md) </span></span>  
 <span data-ttu-id="c9cbb-112">[Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md) </span><span class="sxs-lookup"><span data-stu-id="c9cbb-112">[Network Programming Samples](../../../docs/framework/network-programming/network-programming-samples.md) </span></span>  
 <span data-ttu-id="c9cbb-113">[Amostra de tecnologia de cliente FTP](http://go.microsoft.com/fwlink/?LinkID=179557) </span><span class="sxs-lookup"><span data-stu-id="c9cbb-113">[FTP Client Technology Sample](http://go.microsoft.com/fwlink/?LinkID=179557) </span></span>  
 <span data-ttu-id="c9cbb-114">[Amostra de tecnologia do Gerenciador de FTP](http://go.microsoft.com/fwlink/?LinkID=179569) </span><span class="sxs-lookup"><span data-stu-id="c9cbb-114">[FTP Explorer Technology Sample](http://go.microsoft.com/fwlink/?LinkID=179569) </span></span>  
 [<span data-ttu-id="c9cbb-115">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="c9cbb-115">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)

