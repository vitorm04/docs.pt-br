---
title: Método ICLRRuntimeInfo::GetProcAddress
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a95b6b7e20bbcd86dedf187c932f2cf74d37cdab
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199174"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="5cc71-102">Método ICLRRuntimeInfo::GetProcAddress</span><span class="sxs-lookup"><span data-stu-id="5cc71-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="5cc71-103">Obtém o endereço de uma função especificada exportada do common language runtime (CLR) associado a essa interface.</span><span class="sxs-lookup"><span data-stu-id="5cc71-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="5cc71-104">Esse método substitui o [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="5cc71-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc71-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cc71-105">Syntax</span></span>  
  
```  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cc71-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5cc71-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="5cc71-107">[in] O nome da função exportada.</span><span class="sxs-lookup"><span data-stu-id="5cc71-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="5cc71-108">[out] O endereço da função exportada.</span><span class="sxs-lookup"><span data-stu-id="5cc71-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5cc71-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5cc71-109">Return Value</span></span>  
 <span data-ttu-id="5cc71-110">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="5cc71-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="5cc71-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5cc71-111">HRESULT</span></span>|<span data-ttu-id="5cc71-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5cc71-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5cc71-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5cc71-113">S_OK</span></span>|<span data-ttu-id="5cc71-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="5cc71-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="5cc71-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="5cc71-115">E_POINTER</span></span>|<span data-ttu-id="5cc71-116">`pszProcName` ou `ppProc` é nulo.</span><span class="sxs-lookup"><span data-stu-id="5cc71-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="5cc71-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="5cc71-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="5cc71-118">A função especificada não é uma função exportada.</span><span class="sxs-lookup"><span data-stu-id="5cc71-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5cc71-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="5cc71-119">Remarks</span></span>  
 <span data-ttu-id="5cc71-120">Esse método faz com que o CLR a ser carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="5cc71-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cc71-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5cc71-121">Requirements</span></span>  
 <span data-ttu-id="5cc71-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cc71-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cc71-123">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5cc71-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5cc71-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5cc71-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5cc71-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cc71-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc71-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cc71-126">See also</span></span>

- [<span data-ttu-id="5cc71-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="5cc71-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="5cc71-128">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="5cc71-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="5cc71-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="5cc71-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
