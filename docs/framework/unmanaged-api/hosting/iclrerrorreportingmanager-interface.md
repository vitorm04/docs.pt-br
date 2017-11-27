---
title: Interface ICLRErrorReportingManager
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager
helpviewer_keywords: ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590cd87d6a566e9c8c3819fd1b250997938e9c35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="6b007-102">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="6b007-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="6b007-103">Fornece métodos que permitem que o host configurar os despejos de pilha personalizado para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="6b007-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6b007-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="6b007-104">Methods</span></span>  
  
|<span data-ttu-id="6b007-105">Método</span><span class="sxs-lookup"><span data-stu-id="6b007-105">Method</span></span>|<span data-ttu-id="6b007-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="6b007-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6b007-107">Método BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="6b007-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="6b007-108">Especifica a configuração de despejos de pilha personalizado para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="6b007-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="6b007-109">Método EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="6b007-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="6b007-110">Limpa a configuração de despejo de pilha personalizado foi definida por uma chamada anterior para `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="6b007-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="6b007-111">Método GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="6b007-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="6b007-112">Obtém o bucket Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="6b007-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b007-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b007-113">Remarks</span></span>  
 <span data-ttu-id="6b007-114">O `BeginCustomDump` método define a configuração de despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="6b007-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="6b007-115">O `EndCustomDump` método limpa a configuração de despejo de pilha personalizado e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="6b007-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="6b007-116">Ele deve ser chamado após a conclusão do despejo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6b007-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6b007-117">Falha ao chamar `EndCustomDump` faz com que a memória vazem.</span><span class="sxs-lookup"><span data-stu-id="6b007-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b007-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b007-118">Requirements</span></span>  
 <span data-ttu-id="6b007-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b007-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b007-120">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6b007-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6b007-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6b007-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6b007-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b007-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b007-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b007-123">See Also</span></span>  
 [<span data-ttu-id="6b007-124">Enumeração ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="6b007-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="6b007-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="6b007-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
