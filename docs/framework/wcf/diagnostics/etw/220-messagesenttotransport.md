---
title: 220 - MessageSentToTransport
ms.date: 03/30/2017
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
ms.openlocfilehash: 92ec664aead15470fbed576bf157d64d984ddebf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460428"
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="8426c-102">220 - MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="8426c-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="8426c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8426c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8426c-104">Id</span><span class="sxs-lookup"><span data-stu-id="8426c-104">Id</span></span>|<span data-ttu-id="8426c-105">220</span><span class="sxs-lookup"><span data-stu-id="8426c-105">220</span></span>|  
|<span data-ttu-id="8426c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8426c-106">Keywords</span></span>|<span data-ttu-id="8426c-107">EndToEndMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8426c-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8426c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8426c-108">Level</span></span>|<span data-ttu-id="8426c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="8426c-109">Information</span></span>|  
|<span data-ttu-id="8426c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8426c-110">Channel</span></span>|<span data-ttu-id="8426c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="8426c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8426c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8426c-112">Description</span></span>  
 <span data-ttu-id="8426c-113">Esse evento é emitido quando o modelo de serviço envia uma mensagem para o transporte.</span><span class="sxs-lookup"><span data-stu-id="8426c-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8426c-114">Esse evento não será emitido para transportes unidirecionais.</span><span class="sxs-lookup"><span data-stu-id="8426c-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8426c-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8426c-115">Message</span></span>  
 <span data-ttu-id="8426c-116">O Dispatcher enviou uma mensagem para o transporte.</span><span class="sxs-lookup"><span data-stu-id="8426c-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="8426c-117">ID de correlação = = '%1'.</span><span class="sxs-lookup"><span data-stu-id="8426c-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8426c-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8426c-118">Details</span></span>  
  
|<span data-ttu-id="8426c-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="8426c-119">Data Item Name</span></span>|<span data-ttu-id="8426c-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="8426c-120">Data Item Type</span></span>|<span data-ttu-id="8426c-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8426c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8426c-122">ID de correlação</span><span class="sxs-lookup"><span data-stu-id="8426c-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="8426c-123">A atividade de ID usada para correlacionar uma `MessageSentToTransport` evento em um serviço ou cliente correspondente `MessageReceivedFromTransport` na outra extremidade.</span><span class="sxs-lookup"><span data-stu-id="8426c-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="8426c-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="8426c-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="8426c-125">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="8426c-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8426c-126">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="8426c-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8426c-127">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8426c-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8426c-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8426c-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8426c-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8426c-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
