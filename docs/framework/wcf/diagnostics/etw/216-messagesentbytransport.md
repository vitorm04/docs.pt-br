---
title: 216 - MessageSentByTransport
ms.date: 03/30/2017
ms.assetid: 150c3167-4154-4225-8d94-57cc94341233
ms.openlocfilehash: fa21568e4c8c38eefe359c417d47ec0a9d30a7c4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781804"
---
# <a name="216---messagesentbytransport"></a><span data-ttu-id="8c88c-102">216 - MessageSentByTransport</span><span class="sxs-lookup"><span data-stu-id="8c88c-102">216 - MessageSentByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="8c88c-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="8c88c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8c88c-104">ID</span><span class="sxs-lookup"><span data-stu-id="8c88c-104">ID</span></span>|<span data-ttu-id="8c88c-105">216</span><span class="sxs-lookup"><span data-stu-id="8c88c-105">216</span></span>|  
|<span data-ttu-id="8c88c-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="8c88c-106">Keywords</span></span>|<span data-ttu-id="8c88c-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8c88c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8c88c-108">Nível</span><span class="sxs-lookup"><span data-stu-id="8c88c-108">Level</span></span>|<span data-ttu-id="8c88c-109">Informações</span><span class="sxs-lookup"><span data-stu-id="8c88c-109">Information</span></span>|  
|<span data-ttu-id="8c88c-110">Canal</span><span class="sxs-lookup"><span data-stu-id="8c88c-110">Channel</span></span>|<span data-ttu-id="8c88c-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="8c88c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8c88c-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c88c-112">Description</span></span>  
 <span data-ttu-id="8c88c-113">Esse evento ocorre quando um transporte de TCP envia uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="8c88c-113">This event occurs when a TCP-based transport sends a message.</span></span> <span data-ttu-id="8c88c-114">Observe que no nível do transporte várias mensagens podem ser trocadas entre clientes e serviços para uma única operação.</span><span class="sxs-lookup"><span data-stu-id="8c88c-114">Note that at the transport level multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="8c88c-115">Isso pode ser devido ao comportamento de infraestrutura, segurança, sendo um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="8c88c-115">This may be due to infrastructure behavior, security being a good example.</span></span> <span data-ttu-id="8c88c-116">Portanto, o número de **MessageSentByTransport** eventos que são emitidos variam com base na associação do seu serviço e sua configuração.</span><span class="sxs-lookup"><span data-stu-id="8c88c-116">Therefore, the number of **MessageSentByTransport** events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8c88c-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="8c88c-117">Message</span></span>  
 <span data-ttu-id="8c88c-118">O transporte enviou uma mensagem para '%1'.</span><span class="sxs-lookup"><span data-stu-id="8c88c-118">The transport sent a message to '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8c88c-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8c88c-119">Details</span></span>  
  
|<span data-ttu-id="8c88c-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="8c88c-120">Data Item Name</span></span>|<span data-ttu-id="8c88c-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="8c88c-121">Data Item Type</span></span>|<span data-ttu-id="8c88c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="8c88c-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8c88c-123">DestinationAddress</span><span class="sxs-lookup"><span data-stu-id="8c88c-123">DestinationAddress</span></span>|`xs:string`|<span data-ttu-id="8c88c-124">O endereço que recebeu a mensagem de solicitação.</span><span class="sxs-lookup"><span data-stu-id="8c88c-124">The address that the request message was sent to.</span></span>|  
|<span data-ttu-id="8c88c-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="8c88c-125">HostReference</span></span>|<span data-ttu-id="8c88c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="8c88c-126">xs:string</span></span>|<span data-ttu-id="8c88c-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="8c88c-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8c88c-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="8c88c-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8c88c-129">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="8c88c-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8c88c-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8c88c-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8c88c-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="8c88c-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
