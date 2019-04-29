---
title: 206 - ErrorHandlerInvoked
ms.date: 03/30/2017
ms.assetid: 97340f4d-4e09-4e42-a17a-982b3868dbcf
ms.openlocfilehash: 40a92d77c57728249569a854eab8767ff371bca2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781921"
---
# <a name="206---errorhandlerinvoked"></a><span data-ttu-id="0077e-102">206 - ErrorHandlerInvoked</span><span class="sxs-lookup"><span data-stu-id="0077e-102">206 - ErrorHandlerInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="0077e-103">Propriedades</span><span class="sxs-lookup"><span data-stu-id="0077e-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0077e-104">ID</span><span class="sxs-lookup"><span data-stu-id="0077e-104">ID</span></span>|<span data-ttu-id="0077e-105">206</span><span class="sxs-lookup"><span data-stu-id="0077e-105">206</span></span>|  
|<span data-ttu-id="0077e-106">Palavras-chave</span><span class="sxs-lookup"><span data-stu-id="0077e-106">Keywords</span></span>|<span data-ttu-id="0077e-107">Solução de problemas, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0077e-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="0077e-108">Nível</span><span class="sxs-lookup"><span data-stu-id="0077e-108">Level</span></span>|<span data-ttu-id="0077e-109">Informações</span><span class="sxs-lookup"><span data-stu-id="0077e-109">Information</span></span>|  
|<span data-ttu-id="0077e-110">Canal</span><span class="sxs-lookup"><span data-stu-id="0077e-110">Channel</span></span>|<span data-ttu-id="0077e-111">Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico</span><span class="sxs-lookup"><span data-stu-id="0077e-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="0077e-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="0077e-112">Description</span></span>  
 <span data-ttu-id="0077e-113">Esse evento é emitido após um `ErrorHandler` tenha tido a oportunidade de manipular uma exceção que ocorreu em uma operação de serviço.</span><span class="sxs-lookup"><span data-stu-id="0077e-113">This event is emitted after an `ErrorHandler` has had an opportunity to handle an exception that occurred in a service operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="0077e-114">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0077e-114">Message</span></span>  
 <span data-ttu-id="0077e-115">O Dispatcher invocado um ErrorHandler do tipo '%1' com uma exceção do tipo '%3'.</span><span class="sxs-lookup"><span data-stu-id="0077e-115">The Dispatcher invoked an ErrorHandler of type '%1' with an exception of type '%3'.</span></span> <span data-ttu-id="0077e-116">ErrorHandled = = '%2'.</span><span class="sxs-lookup"><span data-stu-id="0077e-116">ErrorHandled == '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="0077e-117">Detalhes</span><span class="sxs-lookup"><span data-stu-id="0077e-117">Details</span></span>  
  
|<span data-ttu-id="0077e-118">Nome do item de dados</span><span class="sxs-lookup"><span data-stu-id="0077e-118">Data Item Name</span></span>|<span data-ttu-id="0077e-119">Tipo de item de dados</span><span class="sxs-lookup"><span data-stu-id="0077e-119">Data Item Type</span></span>|<span data-ttu-id="0077e-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0077e-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="0077e-121">NomeDoTipo</span><span class="sxs-lookup"><span data-stu-id="0077e-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="0077e-122">O FullName do CLR do tipo de chamada `ErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="0077e-122">The CLR FullName of the type of the invoked `ErrorHandler`.</span></span>|  
|<span data-ttu-id="0077e-123">Tratado</span><span class="sxs-lookup"><span data-stu-id="0077e-123">Handled</span></span>|`xs:unsignedByte`|<span data-ttu-id="0077e-124">`true` Se o manipulador de erro manipulado o erro, caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="0077e-124">`true` if the error handler handled the error, otherwise `false`.</span></span>|  
|<span data-ttu-id="0077e-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="0077e-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="0077e-126">O FullName de CLR da exceção que estava sendo manipulada.</span><span class="sxs-lookup"><span data-stu-id="0077e-126">The CLR FullName of the exception that was being handled.</span></span>|  
|<span data-ttu-id="0077e-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="0077e-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="0077e-128">Para serviços hospedados na Web, este campo identifica exclusivamente o serviço na hierarquia da Web.</span><span class="sxs-lookup"><span data-stu-id="0077e-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="0077e-129">O formato é definido como ' caminho Virtual do aplicativo de nome de Site&#124;caminho Virtual de serviço&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="0077e-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="0077e-130">Exemplo: ' Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="0077e-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="0077e-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="0077e-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="0077e-132">A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="0077e-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
