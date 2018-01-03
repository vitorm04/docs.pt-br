---
title: HTTP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- protocols, HTTP
- sending data, HTTP
- HttpWebResponse class, sending and receiving data
- HTTP
- receiving data, HTTP
- application protocols, HTTP
- Internet, HTTP
- network resources, HTTP
- HTTP, about HTTP
- HttpWebRequest class, sending and receiving data
ms.assetid: 985fe5d8-eb71-4024-b361-41fbdc1618d8
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: f72a77e19d04c0dd55887628033f7c975ac3ff25
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="http"></a><span data-ttu-id="8ebab-102">HTTP</span><span class="sxs-lookup"><span data-stu-id="8ebab-102">HTTP</span></span>
<span data-ttu-id="8ebab-103">O .NET Framework fornece suporte abrangente para o protocolo HTTP, que faz com que a maioria dos todo o tráfego de Internet, com o <xref:System.Net.HttpWebRequest> e <xref:System.Net.HttpWebResponse> classes.</span><span class="sxs-lookup"><span data-stu-id="8ebab-103">The .NET Framework provides comprehensive support for the HTTP protocol, which makes up the majority of all Internet traffic, with the <xref:System.Net.HttpWebRequest> and <xref:System.Net.HttpWebResponse> classes.</span></span> <span data-ttu-id="8ebab-104">Essas classes, derivadas de <xref:System.Net.WebRequest> e <xref:System.Net.WebResponse>, são retornadas por padrão sempre que o método estático <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encontra um URI começando com "http" ou "https".</span><span class="sxs-lookup"><span data-stu-id="8ebab-104">These classes, derived from <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse>, are returned by default whenever the static method <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> encounters a URI beginning with "http" or "https".</span></span> <span data-ttu-id="8ebab-105">Na maioria dos casos, as classes **WebRequest** e **WebResponse** fornecem tudo o que é necessário para fazer a solicitação, mas se você precisar acessar os recursos específicos ao HTTP expostos como propriedades, poderá fazer a conversão de tipo dessas classes em **HttpWebRequest** ou **HttpWebResponse**.</span><span class="sxs-lookup"><span data-stu-id="8ebab-105">In most cases, the **WebRequest** and **WebResponse** classes provide all that is necessary to make the request, but if you need access to the HTTP-specific features exposed as properties, you can typecast these classes to **HttpWebRequest** or **HttpWebResponse**.</span></span>  
  
 <span data-ttu-id="8ebab-106">**HttpWebRequest** e **HttpWebResponse** encapsulam uma transação de solicitação e resposta HTTP padrão e fornecem acesso a cabeçalhos HTTP comuns.</span><span class="sxs-lookup"><span data-stu-id="8ebab-106">**HttpWebRequest** and **HttpWebResponse** encapsulate a standard HTTP request-and-response transaction and provide access to common HTTP headers.</span></span> <span data-ttu-id="8ebab-107">Essas classes também dão suporte à maioria dos recursos de HTTP 1.1, incluindo pipelining, envio e recebimento de dados em partes, autenticação, pré-autenticação, criptografia, suporte a proxy, validação de certificado do servidor e gerenciamento de conexão.</span><span class="sxs-lookup"><span data-stu-id="8ebab-107">These classes also support most HTTP 1.1 features, including pipelining, sending and receiving data in chunks, authentication, preauthentication, encryption, proxy support, server certificate validation, and connection management.</span></span> <span data-ttu-id="8ebab-108">Cabeçalhos personalizados e cabeçalhos não fornecidos por meio de propriedades podem ser armazenados em e acessados por meio da propriedade **Headers**.</span><span class="sxs-lookup"><span data-stu-id="8ebab-108">Custom headers and headers not provided through properties can be stored in and accessed through the **Headers** property.</span></span>  
  
 <span data-ttu-id="8ebab-109">**HttpWebRequest** é a classe padrão usada pelo **WebRequest** e não precisa ser registrada antes que você possa passar um URI para o método **WebRequest**.</span><span class="sxs-lookup"><span data-stu-id="8ebab-109">**HttpWebRequest** is the default class used by **WebRequest** and does not need to be registered before you can pass a URI to the **WebRequest.Create** method.</span></span>  
  
 <span data-ttu-id="8ebab-110">Você pode fazer com que o aplicativo siga redirecionamentos HTTP automaticamente definindo a propriedade <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> como **true** (o padrão).</span><span class="sxs-lookup"><span data-stu-id="8ebab-110">You can make your application follow HTTP redirects automatically by setting the <xref:System.Net.HttpWebRequest.AllowAutoRedirect%2A> property to **true** (the default).</span></span> <span data-ttu-id="8ebab-111">O aplicativo redirecionará as solicitações e a propriedade <xref:System.Net.HttpWebResponse.ResponseUri%2A> de **HttpWebResponse** conterá o recurso da Web real que tiver respondido à solicitação.</span><span class="sxs-lookup"><span data-stu-id="8ebab-111">The application will redirect requests, and the <xref:System.Net.HttpWebResponse.ResponseUri%2A> property of **HttpWebResponse** will contain the actual Web resource that responded to the request.</span></span> <span data-ttu-id="8ebab-112">Se você definir **AllowAutoRedirect** para **false**, seu aplicativo deverá ser capaz de tratar redirecionamentos como erros de protocolo HTTP.</span><span class="sxs-lookup"><span data-stu-id="8ebab-112">If you set **AllowAutoRedirect** to **false**, your application must be able to handle redirects as HTTP protocol errors.</span></span>  
  
 <span data-ttu-id="8ebab-113">Aplicativos recebem erros de protocolo HTTP capturando uma <xref:System.Net.WebException> com o <xref:System.Net.WebException.Status%2A> definido como <xref:System.Net.WebExceptionStatus>.</span><span class="sxs-lookup"><span data-stu-id="8ebab-113">Applications receive HTTP protocol errors by catching a <xref:System.Net.WebException> with the <xref:System.Net.WebException.Status%2A> set to <xref:System.Net.WebExceptionStatus>.</span></span> <span data-ttu-id="8ebab-114">A propriedade <xref:System.Net.WebException.Response%2A> contém a **WebResponse** enviada pelo servidor e indica o erro HTTP real encontrado.</span><span class="sxs-lookup"><span data-stu-id="8ebab-114">The <xref:System.Net.WebException.Response%2A> property contains the **WebResponse** sent by the server and indicates the actual HTTP error encountered.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ebab-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ebab-115">See Also</span></span>  
 [<span data-ttu-id="8ebab-116">Acessando a Internet por meio de um proxy</span><span class="sxs-lookup"><span data-stu-id="8ebab-116">Accessing the Internet Through a Proxy</span></span>](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [<span data-ttu-id="8ebab-117">Usando protocolos de aplicativo</span><span class="sxs-lookup"><span data-stu-id="8ebab-117">Using Application Protocols</span></span>](../../../docs/framework/network-programming/using-application-protocols.md)  
 [<span data-ttu-id="8ebab-118">Como acessar propriedades específicas de HTTP</span><span class="sxs-lookup"><span data-stu-id="8ebab-118">How to: Access HTTP-Specific Properties</span></span>](../../../docs/framework/network-programming/how-to-access-http-specific-properties.md)
