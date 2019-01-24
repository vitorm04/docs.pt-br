---
title: Método ICLRRuntimeInfo::LoadLibrary
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.LoadLibrary
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dbcbf1b66793a67c815b420e6d5fe221febe719
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716876"
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="f21a2-102">Método ICLRRuntimeInfo::LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="f21a2-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="f21a2-103">Carrega uma biblioteca do .NET Framework do common language runtime (CLR) representado por um [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="f21a2-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="f21a2-104">Esse método substitui o [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="f21a2-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f21a2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f21a2-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f21a2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f21a2-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="f21a2-107">[in] O nome do assembly a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="f21a2-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="f21a2-108">[out] Um identificador para o assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="f21a2-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f21a2-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f21a2-109">Return Value</span></span>  
 <span data-ttu-id="f21a2-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="f21a2-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f21a2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f21a2-111">HRESULT</span></span>|<span data-ttu-id="f21a2-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="f21a2-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f21a2-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="f21a2-113">S_OK</span></span>|<span data-ttu-id="f21a2-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f21a2-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="f21a2-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="f21a2-115">E_POINTER</span></span>|<span data-ttu-id="f21a2-116">`pwzDllName` ou `phndModule` é nulo.</span><span class="sxs-lookup"><span data-stu-id="f21a2-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="f21a2-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f21a2-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="f21a2-118">Não há memória suficiente está disponível para tratar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="f21a2-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f21a2-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="f21a2-119">Remarks</span></span>  
 <span data-ttu-id="f21a2-120">Esse método carrega apenas os DLLs incluídos no pacote redistribuível do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f21a2-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="f21a2-121">Ele não pode carregar os assemblies gerados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f21a2-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f21a2-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f21a2-122">Requirements</span></span>  
 <span data-ttu-id="f21a2-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f21a2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f21a2-124">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f21a2-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f21a2-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f21a2-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f21a2-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f21a2-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f21a2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f21a2-127">See also</span></span>
- [<span data-ttu-id="f21a2-128">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="f21a2-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f21a2-129">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f21a2-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f21a2-130">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="f21a2-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
