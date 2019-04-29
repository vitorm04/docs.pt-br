---
title: 302 - UserDefinedWarningOccurred
ms.date: 03/30/2017
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
ms.openlocfilehash: c70857951309ef54ba460e96e948c9320269d30f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61596746"
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="05c3f-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="05c3f-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="05c3f-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="05c3f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05c3f-104">ID</span><span class="sxs-lookup"><span data-stu-id="05c3f-104">ID</span></span>|<span data-ttu-id="05c3f-105">302</span><span class="sxs-lookup"><span data-stu-id="05c3f-105">302</span></span>|  
|<span data-ttu-id="05c3f-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="05c3f-106">Keywords</span></span>|<span data-ttu-id="05c3f-107">Solução de problemas, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="05c3f-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="05c3f-108">Nível</span><span class="sxs-lookup"><span data-stu-id="05c3f-108">Level</span></span>|<span data-ttu-id="05c3f-109">Aviso</span><span class="sxs-lookup"><span data-stu-id="05c3f-109">Warning</span></span>|  
|<span data-ttu-id="05c3f-110">Canal</span><span class="sxs-lookup"><span data-stu-id="05c3f-110">Channel</span></span>|<span data-ttu-id="05c3f-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="05c3f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="05c3f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="05c3f-112">Description</span></span>  
 <span data-ttu-id="05c3f-113">Esse evento é emitido do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="05c3f-113">This event is emitted from user code.</span></span> <span data-ttu-id="05c3f-114">Os desenvolvedores podem emitir esse evento quando ocorre um evento de aviso personalizado em seus serviços.</span><span class="sxs-lookup"><span data-stu-id="05c3f-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="05c3f-115">Isso pode ser feito usando o <xref:System.Diagnostics.Eventing> APIs.</span><span class="sxs-lookup"><span data-stu-id="05c3f-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="05c3f-116">Além disso, há um exemplo do WCF que envolve essa API e demonstra como emitir corretamente esse evento.</span><span class="sxs-lookup"><span data-stu-id="05c3f-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="05c3f-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="05c3f-117">Message</span></span>  
 <span data-ttu-id="05c3f-118">Nome: '%1', referência: '%2', carga: % 3</span><span class="sxs-lookup"><span data-stu-id="05c3f-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="05c3f-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="05c3f-119">Details</span></span>  
  
|<span data-ttu-id="05c3f-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="05c3f-120">Data Item Name</span></span>|<span data-ttu-id="05c3f-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="05c3f-121">Data Item Type</span></span>|<span data-ttu-id="05c3f-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="05c3f-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="05c3f-123">Nome</span><span class="sxs-lookup"><span data-stu-id="05c3f-123">Name</span></span>|`xs:string`|<span data-ttu-id="05c3f-124">O nome do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="05c3f-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="05c3f-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="05c3f-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="05c3f-126">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="05c3f-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="05c3f-127">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="05c3f-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="05c3f-128">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="05c3f-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="05c3f-129">carga</span><span class="sxs-lookup"><span data-stu-id="05c3f-129">Payload</span></span>|`xs:string`|<span data-ttu-id="05c3f-130">A carga do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="05c3f-130">The user-defined payload of the event.</span></span>|
