---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621017"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="e0cb2-101">Remoção de Ssl3 de TransportDefaults do WCF</span><span class="sxs-lookup"><span data-stu-id="e0cb2-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="e0cb2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e0cb2-102">Details</span></span>

<span data-ttu-id="e0cb2-103">Ao usar NetTcp com segurança de transporte e um tipo de credencial de certificado, o SSL 3 não é mais um protocolo padrão usado para negociar uma conexão segura.</span><span class="sxs-lookup"><span data-stu-id="e0cb2-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="e0cb2-104">Na maioria dos casos, não deve haver impacto nos aplicativos existentes, pois o TLS 1.0 sempre esteve incluído na lista de protocolos para NetTcp.</span><span class="sxs-lookup"><span data-stu-id="e0cb2-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="e0cb2-105">Todos os clientes existentes devem ser capazes de negociar uma conexão usando, no mínimo, o TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="e0cb2-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e0cb2-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e0cb2-106">Suggestion</span></span>

<span data-ttu-id="e0cb2-107">Se Ssl3 for exigido, use um dos seguintes mecanismos de configuração para adicioná-lo à lista de protocolos negociados.</span><span class="sxs-lookup"><span data-stu-id="e0cb2-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span><ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li><span data-ttu-id="e0cb2-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="e0cb2-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span></span></li></ul>

| <span data-ttu-id="e0cb2-109">Name</span><span class="sxs-lookup"><span data-stu-id="e0cb2-109">Name</span></span>    | <span data-ttu-id="e0cb2-110">Valor</span><span class="sxs-lookup"><span data-stu-id="e0cb2-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e0cb2-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="e0cb2-111">Scope</span></span>   |<span data-ttu-id="e0cb2-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e0cb2-112">Edge</span></span>|
|<span data-ttu-id="e0cb2-113">Versão</span><span class="sxs-lookup"><span data-stu-id="e0cb2-113">Version</span></span>|<span data-ttu-id="e0cb2-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="e0cb2-114">4.6.2</span></span>|
|<span data-ttu-id="e0cb2-115">Type</span><span class="sxs-lookup"><span data-stu-id="e0cb2-115">Type</span></span>|<span data-ttu-id="e0cb2-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="e0cb2-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e0cb2-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="e0cb2-117">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
