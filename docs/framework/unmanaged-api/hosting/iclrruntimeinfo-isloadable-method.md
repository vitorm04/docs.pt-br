---
title: Método ICLRRuntimeInfo::IsLoadable
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e60c3b06453e0f447249bddf5d4da5c240576577
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432954"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="523ef-102">Método ICLRRuntimeInfo::IsLoadable</span><span class="sxs-lookup"><span data-stu-id="523ef-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="523ef-103">Indica se o tempo de execução associado a essa interface pode ser carregado no processo atual, levando em consideração outros tempos de execução já podem ser carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="523ef-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="523ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="523ef-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="523ef-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="523ef-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="523ef-106">[out] `true` se esse tempo de execução pode ser carregado no processo atual; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="523ef-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="523ef-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="523ef-107">Return Value</span></span>  
 <span data-ttu-id="523ef-108">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="523ef-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="523ef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="523ef-109">HRESULT</span></span>|<span data-ttu-id="523ef-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="523ef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="523ef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="523ef-111">S_OK</span></span>|<span data-ttu-id="523ef-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="523ef-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="523ef-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="523ef-113">E_POINTER</span></span>|<span data-ttu-id="523ef-114">`pbLoadable` é nulo.</span><span class="sxs-lookup"><span data-stu-id="523ef-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="523ef-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="523ef-115">Remarks</span></span>  
 <span data-ttu-id="523ef-116">Se o tempo de execução de outro já está carregado no processo e o tempo de execução associado a essa interface pode ser carregado para execução lado a lado em processo `pbLoadable` retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="523ef-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="523ef-117">Se os dois tempos de execução não podem ser executado lado a lado em processo, `pbLoadable` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="523ef-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="523ef-118">Por exemplo, o common language runtime (CLR) versão 4 pode executar lado a lado no mesmo processo com CLR versão 2.0 ou versão 1.1 do CLR.</span><span class="sxs-lookup"><span data-stu-id="523ef-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="523ef-119">No entanto, a versão 1.1 do CLR e CLR versão 2.0 não podem executar lado a lado em processo.</span><span class="sxs-lookup"><span data-stu-id="523ef-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="523ef-120">Se nenhum tempo de execução é carregados no processo, este método sempre retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="523ef-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="523ef-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="523ef-121">Requirements</span></span>  
 <span data-ttu-id="523ef-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="523ef-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="523ef-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="523ef-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="523ef-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="523ef-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="523ef-125">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="523ef-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="523ef-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="523ef-126">See Also</span></span>  
 [<span data-ttu-id="523ef-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="523ef-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="523ef-128">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="523ef-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="523ef-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="523ef-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
