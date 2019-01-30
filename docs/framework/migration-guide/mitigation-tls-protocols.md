---
title: 'Mitigação: Protocolos TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abfbea052072f0b90c9d018b520b67878d235701
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506804"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="0f9de-102">Mitigação: Protocolos TLS</span><span class="sxs-lookup"><span data-stu-id="0f9de-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="0f9de-103">Do .NET Framework 4.6 em diante, as classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType> têm permissão para usar um dos três seguintes protocolos: TLS 1.0, TLS 1.1 ou TLS 1.2.</span><span class="sxs-lookup"><span data-stu-id="0f9de-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="0f9de-104">Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.</span><span class="sxs-lookup"><span data-stu-id="0f9de-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="0f9de-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="0f9de-105">Impact</span></span>  
 <span data-ttu-id="0f9de-106">Essa alteração afeta:</span><span class="sxs-lookup"><span data-stu-id="0f9de-106">This change affects:</span></span>  
  
-   <span data-ttu-id="0f9de-107">Qualquer aplicativo que usa o SSL para se comunicar com um servidor HTTPS ou um servidor de soquete usando qualquer um dos seguintes tipos: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> e <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="0f9de-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="0f9de-108">Qualquer aplicativo do lado do servidor que não possa ser atualizado para dar suporte ao Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="0f9de-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="0f9de-109">Redução</span><span class="sxs-lookup"><span data-stu-id="0f9de-109">Mitigation</span></span>  
 <span data-ttu-id="0f9de-110">A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="0f9de-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="0f9de-111">Se não for viável ou se os aplicativos cliente estiverem desfeitos, a classe <xref:System.AppContext> poderá ser usada para recusar esse recurso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="0f9de-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="0f9de-112">De modo programático, usando um snippet de código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f9de-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="0f9de-113">Como o objeto <xref:System.Net.ServicePointManager> foi inicializado apenas uma vez, definir essas configurações de compatibilidade deverá ser a primeira coisa que o aplicativo fará.</span><span class="sxs-lookup"><span data-stu-id="0f9de-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="0f9de-114">Adicionando a seguinte linha à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="0f9de-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="0f9de-115">No entanto, observe que não é recomendável recusar o comportamento padrão, pois isso torna o aplicativo menos seguro.</span><span class="sxs-lookup"><span data-stu-id="0f9de-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f9de-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f9de-116">See also</span></span>
- [<span data-ttu-id="0f9de-117">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="0f9de-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
