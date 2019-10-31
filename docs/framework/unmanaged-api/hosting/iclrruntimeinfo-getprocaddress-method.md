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
ms.openlocfilehash: cedda39aeebc62c6bf43f42ae2daf6f6f515fd27
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120267"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="ef884-102">Método ICLRRuntimeInfo::GetProcAddress</span><span class="sxs-lookup"><span data-stu-id="ef884-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="ef884-103">Obtém o endereço de uma função especificada que foi exportada do Common Language Runtime (CLR) associado a esta interface.</span><span class="sxs-lookup"><span data-stu-id="ef884-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="ef884-104">Esse método substitui a função [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ef884-104">This method supersedes the [GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef884-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ef884-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef884-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ef884-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="ef884-107">no O nome da função exportada.</span><span class="sxs-lookup"><span data-stu-id="ef884-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="ef884-108">fora O endereço da função exportada.</span><span class="sxs-lookup"><span data-stu-id="ef884-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef884-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="ef884-109">Return Value</span></span>  
 <span data-ttu-id="ef884-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="ef884-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="ef884-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ef884-111">HRESULT</span></span>|<span data-ttu-id="ef884-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="ef884-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ef884-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="ef884-113">S_OK</span></span>|<span data-ttu-id="ef884-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="ef884-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="ef884-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="ef884-115">E_POINTER</span></span>|<span data-ttu-id="ef884-116">`pszProcName` ou `ppProc` é nulo.</span><span class="sxs-lookup"><span data-stu-id="ef884-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="ef884-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="ef884-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="ef884-118">A função especificada não é uma função exportada.</span><span class="sxs-lookup"><span data-stu-id="ef884-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef884-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="ef884-119">Remarks</span></span>  
 <span data-ttu-id="ef884-120">Esse método faz com que o CLR seja carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="ef884-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef884-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ef884-121">Requirements</span></span>  
 <span data-ttu-id="ef884-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ef884-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef884-123">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ef884-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ef884-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ef884-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ef884-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef884-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef884-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef884-126">See also</span></span>

- [<span data-ttu-id="ef884-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="ef884-127">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="ef884-128">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="ef884-128">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="ef884-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="ef884-129">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
