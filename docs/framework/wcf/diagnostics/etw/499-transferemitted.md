---
title: 499 - TransferEmitted
ms.date: 03/30/2017
ms.assetid: 07a26434-a7a0-40fc-b5d0-3520a04328ae
ms.openlocfilehash: b1ade828ee6519288165e272e7d9f36fd6aca9ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33469502"
---
# <a name="499---transferemitted"></a><span data-ttu-id="e527b-102">499 - TransferEmitted</span><span class="sxs-lookup"><span data-stu-id="e527b-102">499 - TransferEmitted</span></span>
## <a name="properties"></a><span data-ttu-id="e527b-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="e527b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e527b-104">ID</span><span class="sxs-lookup"><span data-stu-id="e527b-104">ID</span></span>|<span data-ttu-id="e527b-105">499</span><span class="sxs-lookup"><span data-stu-id="e527b-105">499</span></span>|  
|<span data-ttu-id="e527b-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="e527b-106">Keywords</span></span>|<span data-ttu-id="e527b-107">Solução de problemas, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span><span class="sxs-lookup"><span data-stu-id="e527b-107">Troubleshooting, UserEvents, EndToEndMonitoring, ServiceModel, WFTracking, ServiceHost, WCFMessageLogging</span></span>|  
|<span data-ttu-id="e527b-108">Nível</span><span class="sxs-lookup"><span data-stu-id="e527b-108">Level</span></span>|<span data-ttu-id="e527b-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="e527b-109">LogAlways</span></span>|  
|<span data-ttu-id="e527b-110">Canal</span><span class="sxs-lookup"><span data-stu-id="e527b-110">Channel</span></span>|<span data-ttu-id="e527b-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="e527b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e527b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="e527b-112">Description</span></span>  
 <span data-ttu-id="e527b-113">Esse evento é emitido quando ocorre o evento de transferência.</span><span class="sxs-lookup"><span data-stu-id="e527b-113">This event is emitted when the transfer event takes place.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e527b-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="e527b-114">Message</span></span>  
 <span data-ttu-id="e527b-115">Evento de transferência emitido.</span><span class="sxs-lookup"><span data-stu-id="e527b-115">Transfer event emitted.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e527b-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e527b-116">Details</span></span>  
  
|<span data-ttu-id="e527b-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="e527b-117">Data Item Name</span></span>|<span data-ttu-id="e527b-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="e527b-118">Data Item Type</span></span>|<span data-ttu-id="e527b-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="e527b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e527b-120">HostReference</span><span class="sxs-lookup"><span data-stu-id="e527b-120">HostReference</span></span>|`xs:string`|<span data-ttu-id="e527b-121">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="e527b-121">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e527b-122">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="e527b-122">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e527b-123">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="e527b-123">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e527b-124">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e527b-124">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e527b-125">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="e527b-125">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
