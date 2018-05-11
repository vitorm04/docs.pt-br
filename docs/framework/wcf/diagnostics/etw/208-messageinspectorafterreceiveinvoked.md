---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 3499131fcb52f0a0ab6d0e78e165522b7092612f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="25512-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="25512-102">208 - MessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="25512-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="25512-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="25512-104">ID</span><span class="sxs-lookup"><span data-stu-id="25512-104">ID</span></span>|<span data-ttu-id="25512-105">208</span><span class="sxs-lookup"><span data-stu-id="25512-105">208</span></span>|  
|<span data-ttu-id="25512-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="25512-106">Keywords</span></span>|<span data-ttu-id="25512-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="25512-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="25512-108">Nível</span><span class="sxs-lookup"><span data-stu-id="25512-108">Level</span></span>|<span data-ttu-id="25512-109">Informações</span><span class="sxs-lookup"><span data-stu-id="25512-109">Information</span></span>|  
|<span data-ttu-id="25512-110">Canal</span><span class="sxs-lookup"><span data-stu-id="25512-110">Channel</span></span>|<span data-ttu-id="25512-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="25512-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="25512-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="25512-112">Description</span></span>  
 <span data-ttu-id="25512-113">Esse evento é emitido após o modelo de serviço foi invocado o `AfterReceive` método em um Inspetor de mensagem.</span><span class="sxs-lookup"><span data-stu-id="25512-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="25512-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="25512-114">Message</span></span>  
 <span data-ttu-id="25512-115">O Dispatcher invocou 'AfterReceiveReply' em um MessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="25512-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="25512-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="25512-116">Details</span></span>  
  
|<span data-ttu-id="25512-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="25512-117">Data Item Name</span></span>|<span data-ttu-id="25512-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="25512-118">Data Item Type</span></span>|<span data-ttu-id="25512-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="25512-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="25512-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="25512-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="25512-121">O FullName do CLR do tipo de chamada `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="25512-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="25512-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="25512-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="25512-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="25512-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="25512-124">O formato é definido como ' caminho Virtual do aplicativo Web Site nome&#124;caminho Virtual do serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="25512-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="25512-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="25512-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="25512-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="25512-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="25512-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="25512-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
