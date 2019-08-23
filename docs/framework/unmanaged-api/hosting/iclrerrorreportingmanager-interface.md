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
ms.openlocfilehash: 2a9d9cff0360e4eb27584fe0f22c1c20396ff8f0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966252"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="bf4a7-102">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="bf4a7-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="bf4a7-103">Fornece métodos que permitem ao host configurar despejos de pilha personalizados para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf4a7-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bf4a7-104">Methods</span></span>  
  
|<span data-ttu-id="bf4a7-105">Método</span><span class="sxs-lookup"><span data-stu-id="bf4a7-105">Method</span></span>|<span data-ttu-id="bf4a7-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf4a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf4a7-107">Método BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="bf4a7-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="bf4a7-108">Especifica a configuração de despejos de pilha personalizados para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="bf4a7-109">Método EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="bf4a7-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="bf4a7-110">Limpa a configuração de despejo de pilha personalizado que foi definida por uma chamada anterior `BeginCustomDump`para.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="bf4a7-111">Método GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="bf4a7-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="bf4a7-112">Obtém o Bucket do Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf4a7-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf4a7-113">Remarks</span></span>  
 <span data-ttu-id="bf4a7-114">O `BeginCustomDump` método define a configuração de despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="bf4a7-115">O `EndCustomDump` método limpa a configuração de despejo de pilha personalizada e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="bf4a7-116">Ele deve ser chamado após a conclusão do despejo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="bf4a7-117">Falha ao chamar `EndCustomDump` faz com que a memória seja vazada.</span><span class="sxs-lookup"><span data-stu-id="bf4a7-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf4a7-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bf4a7-118">Requirements</span></span>  
 <span data-ttu-id="bf4a7-119">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf4a7-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf4a7-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bf4a7-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bf4a7-121">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bf4a7-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bf4a7-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf4a7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf4a7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf4a7-123">See also</span></span>

- [<span data-ttu-id="bf4a7-124">Enumeração ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="bf4a7-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="bf4a7-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="bf4a7-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
