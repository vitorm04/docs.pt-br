---
title: 'Mitigação: protocolos TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d37326d0278225146d217624508e7c7738375b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388255"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="a08c5-102">Mitigação: protocolos TLS</span><span class="sxs-lookup"><span data-stu-id="a08c5-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="a08c5-103">A partir do .NET Framework 4.6, as classes <xref:System.Net.ServicePointManager?displayProperty=nameWithType> e <xref:System.Net.Security.SslStream?displayProperty=nameWithType> têm permissão para usar um dos três protocolos a seguir: Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="a08c5-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="a08c5-104">Não há suporte para o protocolo SSL 3.0 e a criptografia RC4.</span><span class="sxs-lookup"><span data-stu-id="a08c5-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a08c5-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="a08c5-105">Impact</span></span>  
 <span data-ttu-id="a08c5-106">Essa alteração afeta:</span><span class="sxs-lookup"><span data-stu-id="a08c5-106">This change affects:</span></span>  
  
-   <span data-ttu-id="a08c5-107">Qualquer aplicativo que usa o SSL para se comunicar com um servidor HTTPS ou um servidor de soquete usando qualquer um dos seguintes tipos: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient> e <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="a08c5-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="a08c5-108">Qualquer aplicativo do lado do servidor que não possa ser atualizado para dar suporte ao Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="a08c5-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a08c5-109">Redução</span><span class="sxs-lookup"><span data-stu-id="a08c5-109">Mitigation</span></span>  
 <span data-ttu-id="a08c5-110">A mitigação recomendada é fazer upgrade do aplicativo do lado do servidor para Tls1.0, Tls1.1 ou Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="a08c5-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="a08c5-111">Se não for viável ou se os aplicativos cliente estiverem desfeitos, a classe <xref:System.AppContext> poderá ser usada para recusar esse recurso de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="a08c5-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="a08c5-112">De modo programático, usando um trecho de código como o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a08c5-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="a08c5-113">Como o objeto <xref:System.Net.ServicePointManager> foi inicializado apenas uma vez, definir essas configurações de compatibilidade deverá ser a primeira coisa que o aplicativo fará.</span><span class="sxs-lookup"><span data-stu-id="a08c5-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="a08c5-114">Adicionando a seguinte linha à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="a08c5-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="a08c5-115">No entanto, observe que não é recomendável recusar o comportamento padrão, pois isso torna o aplicativo menos seguro.</span><span class="sxs-lookup"><span data-stu-id="a08c5-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a08c5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a08c5-116">See Also</span></span>  
 [<span data-ttu-id="a08c5-117">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="a08c5-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
