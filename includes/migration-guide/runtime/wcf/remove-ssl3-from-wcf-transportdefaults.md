---
ms.openlocfilehash: a5f4047d70276a90c9d72918a2559fd795feb26e
ms.sourcegitcommit: 261e0c98a111357692b3b63c596edf0cacf72991
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2020
ms.locfileid: "90770815"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="9193d-101">Remoção de Ssl3 de TransportDefaults do WCF</span><span class="sxs-lookup"><span data-stu-id="9193d-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="9193d-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9193d-102">Details</span></span>

<span data-ttu-id="9193d-103">Ao usar NetTcp com segurança de transporte e um tipo de credencial de certificado, o SSL 3 não é mais um protocolo padrão usado para negociar uma conexão segura.</span><span class="sxs-lookup"><span data-stu-id="9193d-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="9193d-104">Na maioria dos casos, não deve haver impacto nos aplicativos existentes, pois o TLS 1.0 sempre esteve incluído na lista de protocolos para NetTcp.</span><span class="sxs-lookup"><span data-stu-id="9193d-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="9193d-105">Todos os clientes existentes devem ser capazes de negociar uma conexão usando, no mínimo, o TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="9193d-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="9193d-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="9193d-106">Suggestion</span></span>

<span data-ttu-id="9193d-107">Se Ssl3 for exigido, use um dos seguintes mecanismos de configuração para adicioná-lo à lista de protocolos negociados.</span><span class="sxs-lookup"><span data-stu-id="9193d-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols>
- [<span data-ttu-id="9193d-108">\<transport> desse \<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9193d-108">\<transport> of \<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)
- [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)

| <span data-ttu-id="9193d-109">Nome</span><span class="sxs-lookup"><span data-stu-id="9193d-109">Name</span></span>    | <span data-ttu-id="9193d-110">Valor</span><span class="sxs-lookup"><span data-stu-id="9193d-110">Value</span></span>   |
|:--------|:--------|
| <span data-ttu-id="9193d-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="9193d-111">Scope</span></span>   | <span data-ttu-id="9193d-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="9193d-112">Edge</span></span>    |
| <span data-ttu-id="9193d-113">Versão</span><span class="sxs-lookup"><span data-stu-id="9193d-113">Version</span></span> | <span data-ttu-id="9193d-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="9193d-114">4.6.2</span></span>   |
| <span data-ttu-id="9193d-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="9193d-115">Type</span></span>    | <span data-ttu-id="9193d-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="9193d-116">Runtime</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="9193d-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="9193d-117">Affected APIs</span></span>

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols`
- `P:System.ServiceModel.TcpTransportSecurity.SslProtocols`

-->
