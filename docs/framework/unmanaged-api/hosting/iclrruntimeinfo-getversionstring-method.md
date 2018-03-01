---
title: "Método ICLRRuntimeInfo::GetVersionString"
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
- ICLRRuntimeInfo.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetVersionString
helpviewer_keywords:
- ICLRRuntimeInfo::GetVersionString method [.NET Framework hosting]
- GetVersionString method, ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 98b097ef-2276-4dd9-8551-b03c972e8179
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ae6f21fac359006b6d2e56fdd4ba50fb18bb972
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="8a5d3-102">Método ICLRRuntimeInfo::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="8a5d3-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="8a5d3-103">Obtém informações de versão de runtime (CLR) de linguagem comum associadas com um determinado [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="8a5d3-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="8a5d3-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="8a5d3-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="8a5d3-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="8a5d3-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="8a5d3-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="8a5d3-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a5d3-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8a5d3-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a5d3-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="8a5d3-109">[out] A versão de compilação do .NET Framework no formato "v*um*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="8a5d3-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="8a5d3-110">*Um*, *B*, e *X* são números decimais que correspondem a versão principal, a versão secundária, e o número de compilação.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="8a5d3-111">*X* é opcional.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-111">*X* is optional.</span></span> <span data-ttu-id="8a5d3-112">Se *X* é não está presente, não há nenhum ponto à direita.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a5d3-113">Esse parâmetro deve corresponder ao nome de diretório para a versão do .NET Framework, como ele aparece em C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="8a5d3-114">Os valores de exemplo são "v 1.0.3705", "v 1.1.4322", "v 2.0.50727" e "v 4.0. *x*", onde *x* depende do número de compilação instalado.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="8a5d3-115">Observe que o prefixo "v" é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="8a5d3-116">[out no] Especifica o tamanho do `pwzBuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="8a5d3-117">Se `pwzBuffer` é `null`, `pchBuffer` retorna o tamanho necessário do `pwzBuffer` para permitir a pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a5d3-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8a5d3-118">Return Value</span></span>  
 <span data-ttu-id="8a5d3-119">Este método retorna a seguintes HRESULTs específicos, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="8a5d3-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a5d3-120">HRESULT</span></span>|<span data-ttu-id="8a5d3-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="8a5d3-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a5d3-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a5d3-122">S_OK</span></span>|<span data-ttu-id="8a5d3-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="8a5d3-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="8a5d3-124">E_POINTER</span></span>|<span data-ttu-id="8a5d3-125">`pwzBuffer` ou `pchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="8a5d3-125">`pwzBuffer` or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a5d3-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8a5d3-126">Requirements</span></span>  
 <span data-ttu-id="8a5d3-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a5d3-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a5d3-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="8a5d3-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8a5d3-129">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="8a5d3-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a5d3-130">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a5d3-130">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a5d3-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8a5d3-131">See Also</span></span>  
 [<span data-ttu-id="8a5d3-132">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="8a5d3-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="8a5d3-133">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="8a5d3-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="8a5d3-134">Interfaces de hospedagem CLR adicionadas ao .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="8a5d3-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="8a5d3-135">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="8a5d3-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
