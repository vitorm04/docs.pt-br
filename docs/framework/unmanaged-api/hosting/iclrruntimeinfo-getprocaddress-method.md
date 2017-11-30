---
title: "Método ICLRRuntimeInfo::GetProcAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetProcAddress
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1b8af06a52a3961bb3e551375350dee849343b3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="5236f-102">Método ICLRRuntimeInfo::GetProcAddress</span><span class="sxs-lookup"><span data-stu-id="5236f-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="5236f-103">Obtém o endereço de uma função específica que foi exportado do common language runtime (CLR) associado a esta interface.</span><span class="sxs-lookup"><span data-stu-id="5236f-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="5236f-104">Esse método substitui o [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="5236f-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5236f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5236f-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5236f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5236f-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="5236f-107">[in] O nome da função exportada.</span><span class="sxs-lookup"><span data-stu-id="5236f-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="5236f-108">[out] O endereço da função exportada.</span><span class="sxs-lookup"><span data-stu-id="5236f-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5236f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5236f-109">Return Value</span></span>  
 <span data-ttu-id="5236f-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="5236f-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5236f-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5236f-111">HRESULT</span></span>|<span data-ttu-id="5236f-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5236f-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5236f-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5236f-113">S_OK</span></span>|<span data-ttu-id="5236f-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="5236f-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5236f-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5236f-115">E_POINTER</span></span>|<span data-ttu-id="5236f-116">`pszProcName` ou `ppProc` é nulo.</span><span class="sxs-lookup"><span data-stu-id="5236f-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="5236f-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="5236f-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="5236f-118">A função especificada não é uma função exportada.</span><span class="sxs-lookup"><span data-stu-id="5236f-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5236f-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="5236f-119">Remarks</span></span>  
 <span data-ttu-id="5236f-120">Este método faz com que o CLR ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="5236f-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5236f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5236f-121">Requirements</span></span>  
 <span data-ttu-id="5236f-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5236f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5236f-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5236f-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5236f-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5236f-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5236f-125">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5236f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5236f-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5236f-126">See Also</span></span>  
 [<span data-ttu-id="5236f-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="5236f-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="5236f-128">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="5236f-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="5236f-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="5236f-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
