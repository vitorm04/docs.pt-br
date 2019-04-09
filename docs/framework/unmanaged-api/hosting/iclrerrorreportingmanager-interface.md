---
title: Interface ICLRErrorReportingManager
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a20b79dd5eda9c431511cc49e7e3adaa9486b2aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59155981"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="9222f-102">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="9222f-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="9222f-103">Fornece métodos que permitem que o host configurar despejos de pilha personalizado para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="9222f-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9222f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9222f-104">Methods</span></span>  
  
|<span data-ttu-id="9222f-105">Método</span><span class="sxs-lookup"><span data-stu-id="9222f-105">Method</span></span>|<span data-ttu-id="9222f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9222f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9222f-107">Método BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="9222f-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="9222f-108">Especifica a configuração de despejos de pilha personalizado para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="9222f-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="9222f-109">Método EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="9222f-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="9222f-110">Limpa a configuração de despejo de pilha personalizado que foi definida por uma chamada anterior para `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="9222f-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="9222f-111">Método GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="9222f-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="9222f-112">Obtém o número de buckets Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="9222f-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9222f-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9222f-113">Remarks</span></span>  
 <span data-ttu-id="9222f-114">O `BeginCustomDump` método define a configuração de despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="9222f-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="9222f-115">O `EndCustomDump` método limpa a configuração de despejo de pilha personalizado e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="9222f-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="9222f-116">Ele deve ser chamado depois que o despejo personalizado for concluído.</span><span class="sxs-lookup"><span data-stu-id="9222f-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9222f-117">Falha ao chamar `EndCustomDump` faz com que a memória de vazar.</span><span class="sxs-lookup"><span data-stu-id="9222f-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9222f-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9222f-118">Requirements</span></span>  
 <span data-ttu-id="9222f-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9222f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9222f-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9222f-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9222f-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9222f-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9222f-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9222f-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9222f-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9222f-123">See also</span></span>

- [<span data-ttu-id="9222f-124">Enumeração ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="9222f-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="9222f-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="9222f-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
