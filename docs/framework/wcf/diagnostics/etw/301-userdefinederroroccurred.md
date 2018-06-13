---
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 6eb80d6f0b20af9aae6e7de5248323088e352b26
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459473"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="f3faf-102">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="f3faf-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="f3faf-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="f3faf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f3faf-104">ID</span><span class="sxs-lookup"><span data-stu-id="f3faf-104">ID</span></span>|<span data-ttu-id="f3faf-105">301</span><span class="sxs-lookup"><span data-stu-id="f3faf-105">301</span></span>|  
|<span data-ttu-id="f3faf-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="f3faf-106">Keywords</span></span>|<span data-ttu-id="f3faf-107">Solução de problemas, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="f3faf-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="f3faf-108">Nível</span><span class="sxs-lookup"><span data-stu-id="f3faf-108">Level</span></span>|<span data-ttu-id="f3faf-109">Erro</span><span class="sxs-lookup"><span data-stu-id="f3faf-109">Error</span></span>|  
|<span data-ttu-id="f3faf-110">Canal</span><span class="sxs-lookup"><span data-stu-id="f3faf-110">Channel</span></span>|<span data-ttu-id="f3faf-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="f3faf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f3faf-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3faf-112">Description</span></span>  
 <span data-ttu-id="f3faf-113">Esse evento é emitido do código do usuário.</span><span class="sxs-lookup"><span data-stu-id="f3faf-113">This event is emitted from user code.</span></span> <span data-ttu-id="f3faf-114">Os desenvolvedores podem emitir esse evento quando ocorre um erro personalizadas em seu serviço.</span><span class="sxs-lookup"><span data-stu-id="f3faf-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="f3faf-115">Isso pode ser feito usando o <xref:System.Diagnostics.Eventing> APIs.</span><span class="sxs-lookup"><span data-stu-id="f3faf-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="f3faf-116">Além disso, há um exemplo do WCF que encapsula essa API e demonstra como emitir corretamente este evento.</span><span class="sxs-lookup"><span data-stu-id="f3faf-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f3faf-117">Mensagem</span><span class="sxs-lookup"><span data-stu-id="f3faf-117">Message</span></span>  
 <span data-ttu-id="f3faf-118">Nome: '%1', referência: '%2', carga: % 3</span><span class="sxs-lookup"><span data-stu-id="f3faf-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="f3faf-119">Detalhes</span><span class="sxs-lookup"><span data-stu-id="f3faf-119">Details</span></span>  
  
|<span data-ttu-id="f3faf-120">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="f3faf-120">Data Item Name</span></span>|<span data-ttu-id="f3faf-121">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="f3faf-121">Data Item Type</span></span>|<span data-ttu-id="f3faf-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3faf-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f3faf-123">Nome</span><span class="sxs-lookup"><span data-stu-id="f3faf-123">Name</span></span>|`xs:string`|<span data-ttu-id="f3faf-124">O nome do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f3faf-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="f3faf-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="f3faf-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="f3faf-126">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="f3faf-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f3faf-127">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="f3faf-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f3faf-128">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="f3faf-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f3faf-129">Carga</span><span class="sxs-lookup"><span data-stu-id="f3faf-129">Payload</span></span>|`xs:string`|<span data-ttu-id="f3faf-130">A carga do evento definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f3faf-130">The user-defined payload of the event.</span></span>|
