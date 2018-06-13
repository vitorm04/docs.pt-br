---
title: 215 - MessageReceivedByTransport
ms.date: 03/30/2017
ms.assetid: bb32aa60-5207-4711-9f08-110e8ac327e5
ms.openlocfilehash: a8ba90b88ef8dbe3c8651bc565da61aae16a0a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460897"
---
# <a name="215---messagereceivedbytransport"></a><span data-ttu-id="43035-102">215 - MessageReceivedByTransport</span><span class="sxs-lookup"><span data-stu-id="43035-102">215 - MessageReceivedByTransport</span></span>
## <a name="properties"></a><span data-ttu-id="43035-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="43035-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="43035-104">ID</span><span class="sxs-lookup"><span data-stu-id="43035-104">ID</span></span>|<span data-ttu-id="43035-105">215</span><span class="sxs-lookup"><span data-stu-id="43035-105">215</span></span>|  
|<span data-ttu-id="43035-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="43035-106">Keywords</span></span>|<span data-ttu-id="43035-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="43035-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="43035-108">Nível</span><span class="sxs-lookup"><span data-stu-id="43035-108">Level</span></span>|<span data-ttu-id="43035-109">Informações</span><span class="sxs-lookup"><span data-stu-id="43035-109">Information</span></span>|  
|<span data-ttu-id="43035-110">Canal</span><span class="sxs-lookup"><span data-stu-id="43035-110">Channel</span></span>|<span data-ttu-id="43035-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="43035-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="43035-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="43035-112">Description</span></span>  
 <span data-ttu-id="43035-113">Esse evento ocorre quando um transporte baseado em TCP recebe uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="43035-113">This event occurs when a TCP-based transport receives a message.</span></span> <span data-ttu-id="43035-114">Observe que, no nível de transporte, várias mensagens podem ser trocadas entre clientes e serviços para uma única operação.</span><span class="sxs-lookup"><span data-stu-id="43035-114">Note that at the transport level, multiple messages can be exchanged between clients and services for a single operation.</span></span> <span data-ttu-id="43035-115">Isso pode ser devido ao comportamento de infraestrutura, a segurança é um bom exemplo.</span><span class="sxs-lookup"><span data-stu-id="43035-115">This can be due to infrastructure behavior, security is a good example.</span></span> <span data-ttu-id="43035-116">Portanto, o número de `MessageReceivedByTransport` eventos que são emitidos variam com base na associação do serviço e sua configuração.</span><span class="sxs-lookup"><span data-stu-id="43035-116">Therefore, the number of `MessageReceivedByTransport` events that are emitted vary based on your service's binding and its configuration.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43035-117">Esse evento não é emitido para transportes unidirecionais.</span><span class="sxs-lookup"><span data-stu-id="43035-117">This event is not emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="43035-118">Mensagem</span><span class="sxs-lookup"><span data-stu-id="43035-118">Message</span></span>  
 <span data-ttu-id="43035-119">O transporte recebeu uma mensagem de '%1'.</span><span class="sxs-lookup"><span data-stu-id="43035-119">The transport received a message from '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="43035-120">Detalhes</span><span class="sxs-lookup"><span data-stu-id="43035-120">Details</span></span>  
  
|<span data-ttu-id="43035-121">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="43035-121">Data Item Name</span></span>|<span data-ttu-id="43035-122">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="43035-122">Data Item Type</span></span>|<span data-ttu-id="43035-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="43035-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="43035-124">Endereço de escuta</span><span class="sxs-lookup"><span data-stu-id="43035-124">Listen Address</span></span>|`xs:string`|<span data-ttu-id="43035-125">O endereço que recebeu a mensagem.</span><span class="sxs-lookup"><span data-stu-id="43035-125">The address that received the message.</span></span>|  
|<span data-ttu-id="43035-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="43035-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="43035-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="43035-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="43035-128">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="43035-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="43035-129">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="43035-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="43035-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="43035-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="43035-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="43035-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
