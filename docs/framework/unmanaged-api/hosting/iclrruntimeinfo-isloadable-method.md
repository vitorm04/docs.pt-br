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
ms.openlocfilehash: 52257b30b8172b80f968df25115956b6995c1552
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101582"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="88ebd-102">Método ICLRRuntimeInfo::IsLoadable</span><span class="sxs-lookup"><span data-stu-id="88ebd-102">ICLRRuntimeInfo::IsLoadable Method</span></span>
<span data-ttu-id="88ebd-103">Indica se o tempo de execução associado a essa interface pode ser carregado no processo atual, levando em consideração outros tempos de execução que já podem ser carregados no processo.</span><span class="sxs-lookup"><span data-stu-id="88ebd-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88ebd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88ebd-104">Syntax</span></span>  
  
```  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88ebd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88ebd-105">Parameters</span></span>  
 `pbLoadable`  
 <span data-ttu-id="88ebd-106">[out] `true` se esse tempo de execução pode ser carregado no processo atual; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="88ebd-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="88ebd-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="88ebd-107">Return Value</span></span>  
 <span data-ttu-id="88ebd-108">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="88ebd-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="88ebd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="88ebd-109">HRESULT</span></span>|<span data-ttu-id="88ebd-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="88ebd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="88ebd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="88ebd-111">S_OK</span></span>|<span data-ttu-id="88ebd-112">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="88ebd-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="88ebd-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="88ebd-113">E_POINTER</span></span>|`pbLoadable` <span data-ttu-id="88ebd-114">é nulo.</span><span class="sxs-lookup"><span data-stu-id="88ebd-114">is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88ebd-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="88ebd-115">Remarks</span></span>  
 <span data-ttu-id="88ebd-116">Se outro runtime já está carregado no processo e o tempo de execução associado a essa interface pode ser carregado para execução lado a lado em processo `pbLoadable` retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="88ebd-116">If another runtime is already loaded into the process and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="88ebd-117">Se os dois tempos de execução não pode ser executado lado a lado em processo, `pbLoadable` retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="88ebd-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="88ebd-118">Por exemplo, o common language runtime (CLR) versão 4 pode executar lado a lado no mesmo processo com o CLR versão 2.0 ou versão 1.1 do CLR.</span><span class="sxs-lookup"><span data-stu-id="88ebd-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="88ebd-119">No entanto, a versão 1.1 do CLR e o CLR versão 2.0 não podem executar lado a lado em processo.</span><span class="sxs-lookup"><span data-stu-id="88ebd-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="88ebd-120">Se não há tempos de execução são carregados no processo, esse método sempre retorna `true`.</span><span class="sxs-lookup"><span data-stu-id="88ebd-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88ebd-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88ebd-121">Requirements</span></span>  
 <span data-ttu-id="88ebd-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88ebd-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88ebd-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="88ebd-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="88ebd-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="88ebd-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="88ebd-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="88ebd-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="88ebd-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88ebd-126">See also</span></span>

- [<span data-ttu-id="88ebd-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="88ebd-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="88ebd-128">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="88ebd-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="88ebd-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="88ebd-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
