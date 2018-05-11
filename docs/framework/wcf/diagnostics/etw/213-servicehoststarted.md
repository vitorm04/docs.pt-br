---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 819efa2e13c94e2c7a16c24f6ba9c7ef2b87ef8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="aa668-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="aa668-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="aa668-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="aa668-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa668-104">ID</span><span class="sxs-lookup"><span data-stu-id="aa668-104">ID</span></span>|<span data-ttu-id="aa668-105">213</span><span class="sxs-lookup"><span data-stu-id="aa668-105">213</span></span>|  
|<span data-ttu-id="aa668-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="aa668-106">Keywords</span></span>|<span data-ttu-id="aa668-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="aa668-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="aa668-108">Nível</span><span class="sxs-lookup"><span data-stu-id="aa668-108">Level</span></span>|<span data-ttu-id="aa668-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="aa668-109">LogAlways</span></span>|  
|<span data-ttu-id="aa668-110">Canal</span><span class="sxs-lookup"><span data-stu-id="aa668-110">Channel</span></span>|<span data-ttu-id="aa668-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="aa668-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aa668-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa668-112">Description</span></span>  
 <span data-ttu-id="aa668-113">Esse evento é emitido quando um host de serviço hospedado da Web é iniciado.</span><span class="sxs-lookup"><span data-stu-id="aa668-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="aa668-114">Isso geralmente acontece quando o serviço está ativado por uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="aa668-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="aa668-115">Ele também pode ocorrer se o serviço está configurado para ser iniciado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="aa668-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aa668-116">Mensagem</span><span class="sxs-lookup"><span data-stu-id="aa668-116">Message</span></span>  
 <span data-ttu-id="aa668-117">ServiceHost iniciado: '%1'.</span><span class="sxs-lookup"><span data-stu-id="aa668-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aa668-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="aa668-118">Details</span></span>  
  
|<span data-ttu-id="aa668-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="aa668-119">Data Item Name</span></span>|<span data-ttu-id="aa668-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="aa668-120">Data Item Type</span></span>|<span data-ttu-id="aa668-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="aa668-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aa668-122">Nome do tipo de serviço</span><span class="sxs-lookup"><span data-stu-id="aa668-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="aa668-123">O FullName do CLR do tipo de implementação do serviço.</span><span class="sxs-lookup"><span data-stu-id="aa668-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="aa668-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="aa668-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="aa668-125">Os serviços hospedados da Web, este campo identificam exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="aa668-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="aa668-126">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="aa668-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="aa668-127">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="aa668-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="aa668-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aa668-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="aa668-129">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aa668-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
