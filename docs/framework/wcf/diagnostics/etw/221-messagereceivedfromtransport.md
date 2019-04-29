---
title: 221 - MessageReceivedFromTransport
ms.date: 03/30/2017
ms.assetid: 4995f0d5-c182-4d97-981f-6951da6df1fb
ms.openlocfilehash: 98dbf2728242fa73b3e54b7cf32f9e227e5251b2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781713"
---
# <a name="221---messagereceivedfromtransport"></a><span data-ttu-id="5af44-102">221 - MessageReceivedFromTransport</span><span class="sxs-lookup"><span data-stu-id="5af44-102">221 - MessageReceivedFromTransport</span></span>
## <a name="properties"></a><span data-ttu-id="5af44-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="5af44-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5af44-104">ID</span><span class="sxs-lookup"><span data-stu-id="5af44-104">ID</span></span>|<span data-ttu-id="5af44-105">221</span><span class="sxs-lookup"><span data-stu-id="5af44-105">221</span></span>|  
|<span data-ttu-id="5af44-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="5af44-106">Keywords</span></span>|<span data-ttu-id="5af44-107">EndToEndMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5af44-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5af44-108">Nível</span><span class="sxs-lookup"><span data-stu-id="5af44-108">Level</span></span>|<span data-ttu-id="5af44-109">Informações</span><span class="sxs-lookup"><span data-stu-id="5af44-109">Information</span></span>|  
|<span data-ttu-id="5af44-110">Canal</span><span class="sxs-lookup"><span data-stu-id="5af44-110">Channel</span></span>|<span data-ttu-id="5af44-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="5af44-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5af44-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5af44-112">Description</span></span>  
 <span data-ttu-id="5af44-113">Esse evento é emitido quando o modelo de serviço recebe uma mensagem de transporte.</span><span class="sxs-lookup"><span data-stu-id="5af44-113">This event is emitted when the Service Model receives a message from the transport.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5af44-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="5af44-114">Message</span></span>  
 <span data-ttu-id="5af44-115">O Dispatcher recebeu uma mensagem de transporte.</span><span class="sxs-lookup"><span data-stu-id="5af44-115">The Dispatcher received a message from the transport.</span></span> <span data-ttu-id="5af44-116">ID de correlação = = '%1'.</span><span class="sxs-lookup"><span data-stu-id="5af44-116">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5af44-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="5af44-117">Details</span></span>  
  
|<span data-ttu-id="5af44-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="5af44-118">Data Item Name</span></span>|<span data-ttu-id="5af44-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="5af44-119">Data Item Type</span></span>|<span data-ttu-id="5af44-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5af44-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5af44-121">ID de correlação</span><span class="sxs-lookup"><span data-stu-id="5af44-121">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="5af44-122">A atividade de ID usado para correlacionar uma `MessageSentToTransport` eventos de um serviço ou cliente para seus respectivos `MessageReceivedFromTransport` na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="5af44-122">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="5af44-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="5af44-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="5af44-124">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="5af44-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5af44-125">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="5af44-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5af44-126">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="5af44-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5af44-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5af44-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5af44-128">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5af44-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
