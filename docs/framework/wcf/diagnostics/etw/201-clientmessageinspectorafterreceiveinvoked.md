---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 96ca318c141d49e2ac5594d5ee101658a2aa8f21
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782027"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="068b1-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="068b1-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="068b1-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="068b1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="068b1-104">ID</span><span class="sxs-lookup"><span data-stu-id="068b1-104">ID</span></span>|<span data-ttu-id="068b1-105">201</span><span class="sxs-lookup"><span data-stu-id="068b1-105">201</span></span>|  
|<span data-ttu-id="068b1-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="068b1-106">Keywords</span></span>|<span data-ttu-id="068b1-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="068b1-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="068b1-108">Nível</span><span class="sxs-lookup"><span data-stu-id="068b1-108">Level</span></span>|<span data-ttu-id="068b1-109">Informações</span><span class="sxs-lookup"><span data-stu-id="068b1-109">Information</span></span>|  
|<span data-ttu-id="068b1-110">Canal</span><span class="sxs-lookup"><span data-stu-id="068b1-110">Channel</span></span>|<span data-ttu-id="068b1-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="068b1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="068b1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="068b1-112">Description</span></span>  
 <span data-ttu-id="068b1-113">Esse evento é emitido depois que o modelo de serviço tenha chamado o `AfterReceiveReply` método em um Inspetor de mensagens do cliente.</span><span class="sxs-lookup"><span data-stu-id="068b1-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="068b1-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="068b1-114">Message</span></span>  
 <span data-ttu-id="068b1-115">O Dispatcher invocado AfterReceiveReply em um ClientMessageInspector do tipo '%1'.</span><span class="sxs-lookup"><span data-stu-id="068b1-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="068b1-116">Detalhes</span><span class="sxs-lookup"><span data-stu-id="068b1-116">Details</span></span>  
  
|<span data-ttu-id="068b1-117">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="068b1-117">Data Item Name</span></span>|<span data-ttu-id="068b1-118">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="068b1-118">Data Item Type</span></span>|<span data-ttu-id="068b1-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="068b1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="068b1-120">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="068b1-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="068b1-121">O FullName do CLR do tipo do Inspetor invocado.</span><span class="sxs-lookup"><span data-stu-id="068b1-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="068b1-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="068b1-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="068b1-123">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="068b1-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="068b1-124">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="068b1-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="068b1-125">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="068b1-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="068b1-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="068b1-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="068b1-127">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="068b1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
