---
title: "Método ICLRRuntimeInfo::LoadLibrary"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.LoadLibrary
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::LoadLibrary
helpviewer_keywords:
- ICLRRuntimeInfo::LoadLibrary method [.NET Framework hosting]
- LoadLibrary method [.NET Framework hosting]
ms.assetid: 4517ada3-4417-4ac5-a150-73da7a87c686
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b688a4f2557c5ab2ef112e13b411e25ad47b8c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfoloadlibrary-method"></a><span data-ttu-id="b34b3-102">Método ICLRRuntimeInfo::LoadLibrary</span><span class="sxs-lookup"><span data-stu-id="b34b3-102">ICLRRuntimeInfo::LoadLibrary Method</span></span>
<span data-ttu-id="b34b3-103">Carrega uma biblioteca do .NET Framework do common language runtime (CLR) representado por um [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="b34b3-103">Loads a .NET Framework library from the common language runtime (CLR) represented by an [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="b34b3-104">Esse método substitui o [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="b34b3-104">This method supersedes the [LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b34b3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b34b3-105">Syntax</span></span>  
  
```  
HRESULT LoadLibrary(  
     [in]  LPCWSTR pwzDllName,  
     [out, retval] HMODULE *phndModule);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b34b3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b34b3-106">Parameters</span></span>  
 `pwzDllName`  
 <span data-ttu-id="b34b3-107">[in] O nome do assembly a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="b34b3-107">[in] The name of the assembly to be loaded.</span></span>  
  
 `phndModule`  
 <span data-ttu-id="b34b3-108">[out] Um identificador para o assembly carregado.</span><span class="sxs-lookup"><span data-stu-id="b34b3-108">[out] A handle to the loaded assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b34b3-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b34b3-109">Return Value</span></span>  
 <span data-ttu-id="b34b3-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="b34b3-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="b34b3-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b34b3-111">HRESULT</span></span>|<span data-ttu-id="b34b3-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b34b3-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b34b3-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b34b3-113">S_OK</span></span>|<span data-ttu-id="b34b3-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="b34b3-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="b34b3-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="b34b3-115">E_POINTER</span></span>|<span data-ttu-id="b34b3-116">`pwzDllName` ou `phndModule` é nulo.</span><span class="sxs-lookup"><span data-stu-id="b34b3-116">`pwzDllName` or `phndModule` is null.</span></span>|  
|<span data-ttu-id="b34b3-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b34b3-117">E_OUTOFMEMORY</span></span>|<span data-ttu-id="b34b3-118">Não há memória suficiente está disponível para tratar a solicitação.</span><span class="sxs-lookup"><span data-stu-id="b34b3-118">Not enough memory is available to handle the request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b34b3-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b34b3-119">Remarks</span></span>  
 <span data-ttu-id="b34b3-120">Esse método carrega apenas DLLs incluídos no pacote redistribuível do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b34b3-120">This method only loads DLLs included in the .NET Framework redistributable package.</span></span> <span data-ttu-id="b34b3-121">Ele não pode carregar os assemblies gerados pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="b34b3-121">It can not load user-generated assemblies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b34b3-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b34b3-122">Requirements</span></span>  
 <span data-ttu-id="b34b3-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b34b3-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b34b3-124">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b34b3-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b34b3-125">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b34b3-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b34b3-126">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b34b3-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b34b3-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b34b3-127">See Also</span></span>  
 [<span data-ttu-id="b34b3-128">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="b34b3-128">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="b34b3-129">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="b34b3-129">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="b34b3-130">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b34b3-130">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
