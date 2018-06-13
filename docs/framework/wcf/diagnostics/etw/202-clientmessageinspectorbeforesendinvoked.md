---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 98de1d7e8e5e87ec7fbd783092f7fbc212fec65d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459349"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="0f263-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="0f263-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0f263-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0f263-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0f263-104">ID</span><span class="sxs-lookup"><span data-stu-id="0f263-104">ID</span></span>|<span data-ttu-id="0f263-105">202</span><span class="sxs-lookup"><span data-stu-id="0f263-105">202</span></span>|  
|<span data-ttu-id="0f263-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0f263-106">Keywords</span></span>|<span data-ttu-id="0f263-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0f263-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0f263-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0f263-108">Level</span></span>|<span data-ttu-id="0f263-109">Informações</span><span class="sxs-lookup"><span data-stu-id="0f263-109">Information</span></span>|  
|<span data-ttu-id="0f263-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0f263-110">Channel</span></span>|<span data-ttu-id="0f263-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="0f263-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0f263-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f263-112">Description</span></span>  
 <span data-ttu-id="0f263-113">Esse evento é emitido após o modelo de serviço foi invocado o `BeforeSendRequest` método em um Inspetor de mensagem do cliente.</span><span class="sxs-lookup"><span data-stu-id="0f263-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0f263-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0f263-114">Message</span></span>  
 <span data-ttu-id="0f263-115">O Dispatcher invocou 'BeforeSendRequest' em um ClientMessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="0f263-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0f263-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0f263-116">Details</span></span>  
  
|<span data-ttu-id="0f263-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0f263-117">Data Item Name</span></span>|<span data-ttu-id="0f263-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0f263-118">Data Item Type</span></span>|<span data-ttu-id="0f263-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f263-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0f263-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="0f263-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="0f263-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="0f263-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="0f263-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="0f263-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="0f263-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="0f263-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0f263-124">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="0f263-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0f263-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="0f263-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0f263-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0f263-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0f263-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0f263-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
