---
title: Método ICLRRuntimeInfo::GetVersionString
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6e320936430307dab066eecc835ac5c84bd22bc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202320"
---
# <a name="iclrruntimeinfogetversionstring-method"></a><span data-ttu-id="0d6bc-102">Método ICLRRuntimeInfo::GetVersionString</span><span class="sxs-lookup"><span data-stu-id="0d6bc-102">ICLRRuntimeInfo::GetVersionString Method</span></span>
<span data-ttu-id="0d6bc-103">Obtém informações de versão de runtime (CLR) de linguagem comum associadas com um determinado [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-103">Gets common language runtime (CLR) version information associated with a given [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="0d6bc-104">Esse método substitui as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="0d6bc-104">This method supersedes the following functions:</span></span>  
  
-   [<span data-ttu-id="0d6bc-105">GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="0d6bc-105">GetRequestedRuntimeInfo</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
  
-   [<span data-ttu-id="0d6bc-106">GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="0d6bc-106">GetRequestedRuntimeVersion</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
## <a name="syntax"></a><span data-ttu-id="0d6bc-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d6bc-107">Syntax</span></span>  
  
```  
HRESULT GetVersionString(  
    [out, size_is(*pcchBuffer)] LPWSTR pwzBuffer,  
    [in, out]  DWORD *pcchBuffer);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d6bc-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0d6bc-108">Parameters</span></span>  
 `pwzBuffer`  
 <span data-ttu-id="0d6bc-109">[out] A versão de compilação do .NET Framework no formato "v*um*. *B*[. *X*] ".</span><span class="sxs-lookup"><span data-stu-id="0d6bc-109">[out] The .NET Framework compilation version in the format "v*A*.*B*[.*X*]".</span></span> <span data-ttu-id="0d6bc-110">*Um*, *B*, e *X* são números decimais que correspondem da versão principal, a versão secundária e o número da compilação.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-110">*A*, *B*, and *X* are decimal numbers that correspond to the major version, the minor version, and the build number.</span></span> <span data-ttu-id="0d6bc-111">*X* é opcional.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-111">*X* is optional.</span></span> <span data-ttu-id="0d6bc-112">Se *X* é não estiver presente, não há nenhum ponto à direita.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-112">If *X* is not present, there is no trailing period.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0d6bc-113">Esse parâmetro deve corresponder ao nome de diretório para a versão do .NET Framework, como ele aparece sob C:\Windows\Microsoft.NET\Framework.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-113">This parameter must match the directory name for the .NET Framework version, as it appears under C:\Windows\Microsoft.NET\Framework.</span></span>  
  
 <span data-ttu-id="0d6bc-114">Os valores de exemplo são "v1.0.3705", "v1.1.4322", "v2.0.50727" e "v4.0. *x*", onde *x* depende do número de compilação instalado.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-114">Example values are "v1.0.3705", "v1.1.4322", "v2.0.50727", and "v4.0.*x*", where *x* depends on the build number installed.</span></span> <span data-ttu-id="0d6bc-115">Observe que o prefixo "v" é obrigatório.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-115">Note that the "v" prefix is mandatory.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="0d6bc-116">[no, out] Especifica o tamanho do `pwzBuffer` para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-116">[in, out] Specifies the size of `pwzBuffer` to avoid buffer overruns.</span></span> <span data-ttu-id="0d6bc-117">Se `pwzBuffer` está `null`, `pchBuffer` retorna o tamanho necessário do `pwzBuffer` para permitir a pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-117">If `pwzBuffer` is `null`, `pchBuffer` returns the required size of `pwzBuffer` to allow preallocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d6bc-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0d6bc-118">Return Value</span></span>  
 <span data-ttu-id="0d6bc-119">Esse método retorna os HRESULTs específicos a seguir, bem como o HRESULT erros que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-119">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="0d6bc-120">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d6bc-120">HRESULT</span></span>|<span data-ttu-id="0d6bc-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d6bc-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d6bc-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d6bc-122">S_OK</span></span>|<span data-ttu-id="0d6bc-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="0d6bc-124">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="0d6bc-124">E_POINTER</span></span>|`pwzBuffer` <span data-ttu-id="0d6bc-125">ou `pchBuffer` é nulo.</span><span class="sxs-lookup"><span data-stu-id="0d6bc-125">or `pchBuffer` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d6bc-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d6bc-126">Requirements</span></span>  
 <span data-ttu-id="0d6bc-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d6bc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d6bc-128">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0d6bc-128">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0d6bc-129">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="0d6bc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="0d6bc-130">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0d6bc-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0d6bc-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d6bc-131">See also</span></span>

- [<span data-ttu-id="0d6bc-132">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="0d6bc-132">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="0d6bc-133">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="0d6bc-133">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="0d6bc-134">Interfaces de hospedagem CLR adicionadas no .NET Framework 4 e 4.5</span><span class="sxs-lookup"><span data-stu-id="0d6bc-134">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="0d6bc-135">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="0d6bc-135">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
