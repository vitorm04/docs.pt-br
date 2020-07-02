---
ms.openlocfilehash: 3aafb14b65f7c0f9e5d77927809547f9d4b96e1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619808"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a><span data-ttu-id="07dfc-101">Códigos de erro de maxRequestLength ou maxReceivedMessageSize são diferentes</span><span class="sxs-lookup"><span data-stu-id="07dfc-101">Error codes for maxRequestLength or maxReceivedMessageSize are different</span></span>

#### <a name="details"></a><span data-ttu-id="07dfc-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="07dfc-102">Details</span></span>

<span data-ttu-id="07dfc-103">Mensagens nos serviços Web WCF hospedadas no IIS (Serviços de Informações da Internet) ou no ASP.NET Development Server que excedam maxRequestLength (no ASP.NET) ou maxReceivedMessageSize (no WCF) têm códigos de erro diferentes. O código de status HTTP foi alterado de 400 (Solicitação Incorreta) para 413 (Entidade de Solicitação Muito Longa), e as mensagens que excederam as configurações de maxRequestLength ou maxReceivedMessageSize lançarão uma exceção <xref:System.ServiceModel.ProtocolException?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="07dfc-103">Messages in WCF web services hosted in Internet Information Services (IIS) or ASP.NET Development Server that exceed maxRequestLength (in ASP.NET) or maxReceivedMessageSize (in WCF) have different error codeThe HTTP status code has changed from 400 (Bad Request) to 413 (Request Entity Too Large), and messages that exceed either the maxRequestLength or the maxReceivedMessageSize setting throw a <xref:System.ServiceModel.ProtocolException?displayProperty=fullName> exception.</span></span> <span data-ttu-id="07dfc-104">Isso inclui os casos em que o modo de transferência é Streamed.</span><span class="sxs-lookup"><span data-stu-id="07dfc-104">This includes cases in which the transfer mode is Streamed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="07dfc-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="07dfc-105">Suggestion</span></span>

<span data-ttu-id="07dfc-106">Essa alteração facilita a depuração nos casos em que o comprimento da mensagem excede os limites permitidos pelo ASP.NET ou WCF. É necessário modificar os códigos que executam o processamento baseado em um código de status HTTP 400.</span><span class="sxs-lookup"><span data-stu-id="07dfc-106">This change facilitates debugging in cases where the message length exceeds the limits allowed by ASP.NET or WCF.You must modify any code that performs processing based on an HTTP 400 status code.</span></span>

| <span data-ttu-id="07dfc-107">Name</span><span class="sxs-lookup"><span data-stu-id="07dfc-107">Name</span></span>    | <span data-ttu-id="07dfc-108">Valor</span><span class="sxs-lookup"><span data-stu-id="07dfc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="07dfc-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="07dfc-109">Scope</span></span>   |<span data-ttu-id="07dfc-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="07dfc-110">Edge</span></span>|
|<span data-ttu-id="07dfc-111">Versão</span><span class="sxs-lookup"><span data-stu-id="07dfc-111">Version</span></span>|<span data-ttu-id="07dfc-112">4.5</span><span class="sxs-lookup"><span data-stu-id="07dfc-112">4.5</span></span>|
|<span data-ttu-id="07dfc-113">Type</span><span class="sxs-lookup"><span data-stu-id="07dfc-113">Type</span></span>|<span data-ttu-id="07dfc-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="07dfc-114">Runtime</span></span>|
