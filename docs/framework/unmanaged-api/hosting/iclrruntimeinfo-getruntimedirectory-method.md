---
title: "Método ICLRRuntimeInfo::GetRuntimeDirectory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetRuntimeDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetRuntimeDirectory
helpviewer_keywords:
- GetRuntimeDirectory method [.NET Framework hosting]
- ICLRRuntimeInfo::GetRuntimeDirectory method [.NET Framework hosting]
ms.assetid: 4401546e-4d48-453f-a1fb-b2ebda54df5c
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f185ed474234a33988e1946b2f69da373096e19b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetruntimedirectory-method"></a><span data-ttu-id="9288d-102">Método ICLRRuntimeInfo::GetRuntimeDirectory</span><span class="sxs-lookup"><span data-stu-id="9288d-102">ICLRRuntimeInfo::GetRuntimeDirectory Method</span></span>
<span data-ttu-id="9288d-103">Obtém o diretório de instalação do common language runtime (CLR) associado a esta interface.</span><span class="sxs-lookup"><span data-stu-id="9288d-103">Gets the installation directory of the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="9288d-104">Esse método substitui o [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) função fornecido nas versões do .NET Framework 2.0, 3.0 e 3.5.</span><span class="sxs-lookup"><span data-stu-id="9288d-104">This method supersedes the [GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md) function provided in the .NET Framework versions 2.0, 3.0, and 3.5.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9288d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9288d-105">Syntax</span></span>  
  
```  
HRESULT GetRuntimeDirectory(  
[out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
[in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9288d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9288d-106">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="9288d-107">[out] Retorna o diretório de instalação do CLR.</span><span class="sxs-lookup"><span data-stu-id="9288d-107">[out] Returns the CLR installation directory.</span></span> <span data-ttu-id="9288d-108">O caminho de instalação é totalmente qualificado; Por exemplo, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span><span class="sxs-lookup"><span data-stu-id="9288d-108">The installation path is fully qualified; for example, "c:\windows\microsoft.net\framework\v1.0.3705\\".</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="9288d-109">[out no] Especifica o tamanho do `pwzBuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="9288d-109">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="9288d-110">Se `pwzBuffer` for nulo, `pchBuffer` retorna o tamanho necessário do `pwzBuffer`.</span><span class="sxs-lookup"><span data-stu-id="9288d-110">If `pwzBuffer` is null, `pchBuffer` returns the required size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9288d-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9288d-111">Return Value</span></span>  
 <span data-ttu-id="9288d-112">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="9288d-112">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="9288d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9288d-113">HRESULT</span></span>|<span data-ttu-id="9288d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="9288d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9288d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="9288d-115">S_OK</span></span>|<span data-ttu-id="9288d-116">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="9288d-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="9288d-117">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="9288d-117">E_POINTER</span></span>|<span data-ttu-id="9288d-118">`pwzBuffer` ou `pchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="9288d-118">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9288d-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="9288d-119">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9288d-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9288d-120">Requirements</span></span>  
 <span data-ttu-id="9288d-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9288d-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9288d-122">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9288d-122">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9288d-123">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="9288d-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9288d-124">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9288d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9288d-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9288d-125">See Also</span></span>  
 [<span data-ttu-id="9288d-126">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="9288d-126">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="9288d-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="9288d-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
