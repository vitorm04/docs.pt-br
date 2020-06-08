---
title: FTP – .NET
description: Saiba mais sobre o suporte abrangente para o protocolo FTP que o .NET Framework fornece usando as classes FtpWebRequest e FtpWebResponse.
ms.date: 03/30/2017
helpviewer_keywords:
- FTP
ms.assetid: 9b43f8b4-89d7-46a7-89fc-71aca916dd32
ms.openlocfilehash: d21ca43cd1041df358dc5e2add9560fb33e85d83
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502581"
---
# <a name="ftp"></a><span data-ttu-id="f40a0-103">FTP</span><span class="sxs-lookup"><span data-stu-id="f40a0-103">FTP</span></span>

<span data-ttu-id="f40a0-104">O .NET Framework fornece suporte abrangente para o protocolo FTP com as classes <xref:System.Net.FtpWebRequest> e <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="f40a0-104">The .NET Framework provides comprehensive support for the FTP protocol with the <xref:System.Net.FtpWebRequest> and <xref:System.Net.FtpWebResponse> classes.</span></span> <span data-ttu-id="f40a0-105">Essas classes são derivadas de <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse>.</span><span class="sxs-lookup"><span data-stu-id="f40a0-105">These classes are derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="f40a0-106">Na maioria dos casos, as classes <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse> fornecem tudo o que é necessário para fazer a solicitação, mas se você precisar acessar os recursos específicos ao FTP expostos como propriedades, poderá fazer a conversão de tipo dessas classes em <xref:System.Net.FtpWebRequest> ou <xref:System.Net.FtpWebResponse>.</span><span class="sxs-lookup"><span data-stu-id="f40a0-106">In most cases, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes provide all that is necessary to make the request, but if you need access to the FTP-specific features exposed as properties, you can typecast these classes to <xref:System.Net.FtpWebRequest> or <xref:System.Net.FtpWebResponse>.</span></span>

## <a name="examples"></a><span data-ttu-id="f40a0-107">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f40a0-107">Examples</span></span>

<span data-ttu-id="f40a0-108">Para obter mais informações, consulte os seguintes tópicos: [Como baixar arquivos com FTP](how-to-download-files-with-ftp.md), [Como carregar arquivos com FTP](how-to-upload-files-with-ftp.md) e [Como listar o conteúdo do diretório com FTP](how-to-list-directory-contents-with-ftp.md).</span><span class="sxs-lookup"><span data-stu-id="f40a0-108">For more information, see the following topics: [How to: Download Files with FTP](how-to-download-files-with-ftp.md), [How to: Upload Files with FTP](how-to-upload-files-with-ftp.md), and [How to: List Directory Contents with FTP](how-to-list-directory-contents-with-ftp.md).</span></span>

## <a name="ftp-and-proxies"></a><span data-ttu-id="f40a0-109">FTP e proxies</span><span class="sxs-lookup"><span data-stu-id="f40a0-109">FTP and proxies</span></span>

<span data-ttu-id="f40a0-110">Se um proxy (especificado pela propriedade <xref:System.Net.FtpWebRequest.Proxy%2A>) for um proxy HTTP, haverá suporte apenas para os comandos <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory> e <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails>.</span><span class="sxs-lookup"><span data-stu-id="f40a0-110">If a proxy (specified by the <xref:System.Net.FtpWebRequest.Proxy%2A> property) is an HTTP proxy, then only the <xref:System.Net.WebRequestMethods.Ftp.DownloadFile>, <xref:System.Net.WebRequestMethods.Ftp.ListDirectory>, and <xref:System.Net.WebRequestMethods.Ftp.ListDirectoryDetails> commands are supported.</span></span>

## <a name="see-also"></a><span data-ttu-id="f40a0-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="f40a0-111">See also</span></span>

- [<span data-ttu-id="f40a0-112">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="f40a0-112">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)
- [<span data-ttu-id="f40a0-113">Amostras de programação de rede</span><span class="sxs-lookup"><span data-stu-id="f40a0-113">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="f40a0-114">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="f40a0-114">Using Application Protocols</span></span>](using-application-protocols.md)
