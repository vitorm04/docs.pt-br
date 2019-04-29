---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 24184c24b9affdf3a56d7968c02cf5354d690749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781869"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="9a0ae-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="9a0ae-102">209 - MessageInspectorBeforeSendInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="9a0ae-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="9a0ae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a0ae-104">ID</span><span class="sxs-lookup"><span data-stu-id="9a0ae-104">ID</span></span>|<span data-ttu-id="9a0ae-105">209</span><span class="sxs-lookup"><span data-stu-id="9a0ae-105">209</span></span>|  
|<span data-ttu-id="9a0ae-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="9a0ae-106">Keywords</span></span>|<span data-ttu-id="9a0ae-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a0ae-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9a0ae-108">Nível</span><span class="sxs-lookup"><span data-stu-id="9a0ae-108">Level</span></span>|<span data-ttu-id="9a0ae-109">Informações</span><span class="sxs-lookup"><span data-stu-id="9a0ae-109">Information</span></span>|  
|<span data-ttu-id="9a0ae-110">Canal</span><span class="sxs-lookup"><span data-stu-id="9a0ae-110">Channel</span></span>|<span data-ttu-id="9a0ae-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="9a0ae-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a0ae-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a0ae-112">Description</span></span>  
 <span data-ttu-id="9a0ae-113">Esse evento é emitido depois que o modelo de serviço tenha chamado o `BeforeSend` método em um Inspetor de mensagens.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a0ae-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="9a0ae-114">Message</span></span>  
 <span data-ttu-id="9a0ae-115">O Dispatcher invocado BeforeSendRequest em um MessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a0ae-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="9a0ae-116">Details</span></span>  
  
|<span data-ttu-id="9a0ae-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="9a0ae-117">Data Item Name</span></span>|<span data-ttu-id="9a0ae-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="9a0ae-118">Data Item Type</span></span>|<span data-ttu-id="9a0ae-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="9a0ae-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a0ae-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="9a0ae-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="9a0ae-121">O FullName do CLR do tipo de chamada `MessageInspector`.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="9a0ae-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="9a0ae-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="9a0ae-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9a0ae-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9a0ae-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9a0ae-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a0ae-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9a0ae-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a0ae-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
