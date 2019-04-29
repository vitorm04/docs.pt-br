---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: eb4289c0346c9e1d9481347d69db8c5f007e4325
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781726"
---
# <a name="219---serviceexception"></a><span data-ttu-id="c8af5-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="c8af5-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="c8af5-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="c8af5-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c8af5-104">ID</span><span class="sxs-lookup"><span data-stu-id="c8af5-104">ID</span></span>|<span data-ttu-id="c8af5-105">219</span><span class="sxs-lookup"><span data-stu-id="c8af5-105">219</span></span>|  
|<span data-ttu-id="c8af5-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="c8af5-106">Keywords</span></span>|<span data-ttu-id="c8af5-107">EndToEndMonitoring, HealthMonitoring, solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c8af5-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c8af5-108">Nível</span><span class="sxs-lookup"><span data-stu-id="c8af5-108">Level</span></span>|<span data-ttu-id="c8af5-109">Erro</span><span class="sxs-lookup"><span data-stu-id="c8af5-109">Error</span></span>|  
|<span data-ttu-id="c8af5-110">Canal</span><span class="sxs-lookup"><span data-stu-id="c8af5-110">Channel</span></span>|<span data-ttu-id="c8af5-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="c8af5-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c8af5-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8af5-112">Description</span></span>  
 <span data-ttu-id="c8af5-113">Esse evento é emitido quando um serviço WCF encontra uma exceção sem tratamento.</span><span class="sxs-lookup"><span data-stu-id="c8af5-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="c8af5-114">Isso inclui exceções sem tratamento durante a ativação, durante o processamento da mensagem e no código do usuário.</span><span class="sxs-lookup"><span data-stu-id="c8af5-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c8af5-115">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c8af5-115">Message</span></span>  
 <span data-ttu-id="c8af5-116">Houve uma exceção sem tratamento do tipo '%2' durante o processamento da mensagem.</span><span class="sxs-lookup"><span data-stu-id="c8af5-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="c8af5-117">ToString completo da exceção: %1.</span><span class="sxs-lookup"><span data-stu-id="c8af5-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c8af5-118">Detalhes</span><span class="sxs-lookup"><span data-stu-id="c8af5-118">Details</span></span>  
  
|<span data-ttu-id="c8af5-119">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="c8af5-119">Data Item Name</span></span>|<span data-ttu-id="c8af5-120">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="c8af5-120">Data Item Type</span></span>|<span data-ttu-id="c8af5-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="c8af5-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c8af5-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="c8af5-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="c8af5-123">O resultado da chamada `ToString`() em que a exceção do CLR.</span><span class="sxs-lookup"><span data-stu-id="c8af5-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="c8af5-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="c8af5-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="c8af5-125">O FullName do CLR do tipo da exceção.</span><span class="sxs-lookup"><span data-stu-id="c8af5-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="c8af5-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c8af5-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c8af5-127">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="c8af5-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c8af5-128">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c8af5-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c8af5-129">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="c8af5-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c8af5-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c8af5-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c8af5-131">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c8af5-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
