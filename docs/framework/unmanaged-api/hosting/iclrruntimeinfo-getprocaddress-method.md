---
title: "Método ICLRRuntimeInfo::GetProcAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2878b23a2f848657e1d26b3bfb8395f8897c0632
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="346ba-102">Método ICLRRuntimeInfo::GetProcAddress</span><span class="sxs-lookup"><span data-stu-id="346ba-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="346ba-103">Obtém o endereço de uma função específica que foi exportado do common language runtime (CLR) associado a esta interface.</span><span class="sxs-lookup"><span data-stu-id="346ba-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="346ba-104">Esse método substitui o [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="346ba-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346ba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="346ba-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="346ba-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="346ba-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="346ba-107">[in] O nome da função exportada.</span><span class="sxs-lookup"><span data-stu-id="346ba-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="346ba-108">[out] O endereço da função exportada.</span><span class="sxs-lookup"><span data-stu-id="346ba-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="346ba-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="346ba-109">Return Value</span></span>  
 <span data-ttu-id="346ba-110">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="346ba-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="346ba-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="346ba-111">HRESULT</span></span>|<span data-ttu-id="346ba-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="346ba-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="346ba-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="346ba-113">S_OK</span></span>|<span data-ttu-id="346ba-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="346ba-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="346ba-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="346ba-115">E_POINTER</span></span>|<span data-ttu-id="346ba-116">`pszProcName` ou `ppProc` é nulo.</span><span class="sxs-lookup"><span data-stu-id="346ba-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="346ba-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="346ba-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="346ba-118">A função especificada não é uma função exportada.</span><span class="sxs-lookup"><span data-stu-id="346ba-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="346ba-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="346ba-119">Remarks</span></span>  
 <span data-ttu-id="346ba-120">Este método faz com que o CLR ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="346ba-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="346ba-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="346ba-121">Requirements</span></span>  
 <span data-ttu-id="346ba-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="346ba-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="346ba-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="346ba-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="346ba-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="346ba-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="346ba-125">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="346ba-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346ba-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="346ba-126">See Also</span></span>  
 [<span data-ttu-id="346ba-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="346ba-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="346ba-128">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="346ba-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="346ba-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="346ba-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
