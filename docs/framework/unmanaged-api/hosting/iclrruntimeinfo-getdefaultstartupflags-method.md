---
title: Método ICLRRuntimeInfo::GetDefaultStartupFlags
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::GetDefaultStartupFlags method [.NET Framework hosting]
- GetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 35c2173e-3b0b-4b2a-950d-e0a01c6df052
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeb4c9935d5e9e4063497dd56276edfe6e62752a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765593"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="645d3-102">Método ICLRRuntimeInfo::GetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="645d3-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="645d3-103">Obtém os sinalizadores de inicialização e o arquivo de configuração de host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="645d3-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="645d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="645d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="645d3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="645d3-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="645d3-106">[out] Um ponteiro para os sinalizadores de inicialização de host que estão atualmente definidas.</span><span class="sxs-lookup"><span data-stu-id="645d3-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="645d3-107">[out] Um ponteiro para o caminho do diretório do arquivo de configuração de host atual.</span><span class="sxs-lookup"><span data-stu-id="645d3-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="645d3-108">[no, out] O tamanho de entrada na `pwzHostConfigFile`, para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="645d3-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="645d3-109">Se `pwzHostConfigFile` é nulo, o método retorna o tamanho necessário do `pwzHostConfigFile` para pré-alocação.</span><span class="sxs-lookup"><span data-stu-id="645d3-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="645d3-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="645d3-110">Return Value</span></span>  
 <span data-ttu-id="645d3-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="645d3-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="645d3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="645d3-112">HRESULT</span></span>|<span data-ttu-id="645d3-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="645d3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="645d3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="645d3-114">S_OK</span></span>|<span data-ttu-id="645d3-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="645d3-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="645d3-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="645d3-116">Remarks</span></span>  
 <span data-ttu-id="645d3-117">Esse método retorna os valores de sinalizador padrão (`STARTUP_CONCURRENT_GC` e `NULL`), ou os valores fornecidos por uma chamada anterior para o [método iclrruntimeinfo:: Setdefaultstartupflags](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), ou os valores definidos por qualquer um do `CorBind*` métodos de se eles estiverem associados a esse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="645d3-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="645d3-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="645d3-118">Requirements</span></span>  
 <span data-ttu-id="645d3-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="645d3-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="645d3-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="645d3-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="645d3-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="645d3-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="645d3-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="645d3-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="645d3-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="645d3-123">See also</span></span>

- [<span data-ttu-id="645d3-124">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="645d3-124">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="645d3-125">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="645d3-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="645d3-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="645d3-126">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
