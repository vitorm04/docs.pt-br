---
ms.openlocfilehash: 26facb645de175d7ef0432394fc2b84f59e8437d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497482"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="ed382-101">Códigos de erro de maxRequestLength ou maxReceivedMessageSize são diferentes</span><span class="sxs-lookup"><span data-stu-id="ed382-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="ed382-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ed382-102">Details</span></span>

<span data-ttu-id="ed382-103">Mensagens nos serviços Web WCF hospedadas no IIS (Serviços de Informações da Internet) ou no ASP.NET Development Server que excedam maxRequestLength (no ASP.NET) ou maxReceivedMessageSize (no WCF) têm códigos de erro diferentes. O código de status HTTP foi alterado de 400 (Solicitação Incorreta) para 413 (Entidade de Solicitação Muito Longa), e as mensagens que excederam as configurações de maxRequestLength ou maxReceivedMessageSize lançarão uma exceção <xref:System.ServiceModel.ProtocolException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="ed382-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="ed382-104">Isso inclui os casos em que o modo de transferência é Streamed.</span><span class="sxs-lookup"><span data-stu-id="ed382-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed382-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ed382-105">Suggestion</span></span>

<span data-ttu-id="ed382-106">Essa alteração facilita a depuração nos casos em que o comprimento da mensagem excede os limites permitidos pelo ASP.NET ou WCF. É necessário modificar os códigos que executam o processamento baseado em um código de status HTTP 400.</span><span class="sxs-lookup"><span data-stu-id="ed382-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="ed382-107">Nome</span><span class="sxs-lookup"><span data-stu-id="ed382-107">Name</span></span>    | <span data-ttu-id="ed382-108">Valor</span><span class="sxs-lookup"><span data-stu-id="ed382-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed382-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="ed382-109">Scope</span></span>   |<span data-ttu-id="ed382-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ed382-110">Edge</span></span>|
|<span data-ttu-id="ed382-111">Versão</span><span class="sxs-lookup"><span data-stu-id="ed382-111">Version</span></span>|<span data-ttu-id="ed382-112">4.5</span><span class="sxs-lookup"><span data-stu-id="ed382-112">4.5</span></span>|
|<span data-ttu-id="ed382-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="ed382-113">Type</span></span>|<span data-ttu-id="ed382-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="ed382-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="ed382-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ed382-115">Affected APIs</span></span>

<span data-ttu-id="ed382-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="ed382-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
