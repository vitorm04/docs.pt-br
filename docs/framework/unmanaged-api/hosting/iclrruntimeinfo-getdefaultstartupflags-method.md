---
title: "Método ICLRRuntimeInfo::GetDefaultStartupFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.GetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73ad12e99a1ba98f6ea61775155cf1389118f754
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="7053d-102">Método ICLRRuntimeInfo::GetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="7053d-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="7053d-103">Obtém os sinalizadores de inicialização e o arquivo de configuração de host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7053d-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7053d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7053d-104">Syntax</span></span>  
  
```  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7053d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7053d-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="7053d-106">[out] Um ponteiro para os sinalizadores de inicialização do host que estão atualmente definidas.</span><span class="sxs-lookup"><span data-stu-id="7053d-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="7053d-107">[out] Um ponteiro para o caminho do diretório do arquivo de configuração de host atual.</span><span class="sxs-lookup"><span data-stu-id="7053d-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="7053d-108">[out no] Na entrada, o tamanho de `pwzHostConfigFile`, para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="7053d-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="7053d-109">Se `pwzHostConfigFile` é null, o método retorna o tamanho necessário do `pwzHostConfigFile` de pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="7053d-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7053d-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7053d-110">Return Value</span></span>  
 <span data-ttu-id="7053d-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="7053d-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="7053d-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7053d-112">HRESULT</span></span>|<span data-ttu-id="7053d-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="7053d-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7053d-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7053d-114">S_OK</span></span>|<span data-ttu-id="7053d-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="7053d-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7053d-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="7053d-116">Remarks</span></span>  
 <span data-ttu-id="7053d-117">Este método retorna os valores de sinalizador padrão (`STARTUP_CONCURRENT_GC` e `NULL`), ou os valores fornecidos por uma chamada anterior a [: Setdefaultstartupflags método](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), ou os valores definidos por qualquer uma da `CorBind*` métodos se eles estiverem associados a esse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7053d-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7053d-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7053d-118">Requirements</span></span>  
 <span data-ttu-id="7053d-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7053d-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7053d-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7053d-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7053d-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7053d-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7053d-122">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7053d-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7053d-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7053d-123">See Also</span></span>  
 [<span data-ttu-id="7053d-124">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="7053d-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="7053d-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="7053d-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="7053d-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="7053d-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
