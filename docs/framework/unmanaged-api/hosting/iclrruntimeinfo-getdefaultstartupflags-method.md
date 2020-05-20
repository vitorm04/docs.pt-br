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
ms.openlocfilehash: 8513787f48ae89632816face386bbcda20555dac
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703876"
---
# <a name="iclrruntimeinfogetdefaultstartupflags-method"></a><span data-ttu-id="c2cea-102">Método ICLRRuntimeInfo::GetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="c2cea-102">ICLRRuntimeInfo::GetDefaultStartupFlags Method</span></span>
<span data-ttu-id="c2cea-103">Obtém os sinalizadores de inicialização e o arquivo de configuração do host que serão usados para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2cea-103">Gets the startup flags and host configuration file that will be used to start the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2cea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2cea-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultStartupFlags(  
     [out]  DWORD *pdwStartupFlags,  
     [out, size_is(*pcchHostConfigFile)] LPWSTR pwzHostConfigFile,  
     [in, out]  DWORD *pcchHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2cea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2cea-105">Parameters</span></span>  
 `pdwStartupFlags`  
 <span data-ttu-id="c2cea-106">fora Um ponteiro para os sinalizadores de inicialização do host que estão atualmente definidos.</span><span class="sxs-lookup"><span data-stu-id="c2cea-106">[out] A pointer to the host startup flags that are currently set.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="c2cea-107">fora Um ponteiro para o caminho do diretório do arquivo de configuração do host atual.</span><span class="sxs-lookup"><span data-stu-id="c2cea-107">[out] A pointer to the directory path of the current host configuration file.</span></span>  
  
 `pcchHostConfigFile`  
 <span data-ttu-id="c2cea-108">[entrada, saída] Na entrada, o tamanho de `pwzHostConfigFile` , para evitar estouros de buffer.</span><span class="sxs-lookup"><span data-stu-id="c2cea-108">[in, out] On input, the size of `pwzHostConfigFile`, to avoid buffer overruns.</span></span> <span data-ttu-id="c2cea-109">Se `pwzHostConfigFile` for NULL, o método retornará o tamanho necessário de `pwzHostConfigFile` pre-Alloc.</span><span class="sxs-lookup"><span data-stu-id="c2cea-109">If `pwzHostConfigFile` is null, the method returns the required size of `pwzHostConfigFile` for pre-allocation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2cea-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2cea-110">Return Value</span></span>  
 <span data-ttu-id="c2cea-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="c2cea-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="c2cea-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c2cea-112">HRESULT</span></span>|<span data-ttu-id="c2cea-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2cea-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c2cea-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="c2cea-114">S_OK</span></span>|<span data-ttu-id="c2cea-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="c2cea-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2cea-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2cea-116">Remarks</span></span>  
 <span data-ttu-id="c2cea-117">Esse método retorna os valores de sinalizador padrão ( `STARTUP_CONCURRENT_GC` e `NULL` ) ou os valores fornecidos por uma chamada anterior para o [método ICLRRuntimeInfo:: SetDefaultStartupFlags](iclrruntimeinfo-setdefaultstartupflags-method.md)ou os valores definidos por qualquer um dos `CorBind*` métodos se eles estiverem associados a esse tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="c2cea-117">This method returns the default flag values (`STARTUP_CONCURRENT_GC` and `NULL`), or the values provided by a previous call to the [ICLRRuntimeInfo::SetDefaultStartupFlags method](iclrruntimeinfo-setdefaultstartupflags-method.md), or the values set by any of the `CorBind*` methods if they are bound to this runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2cea-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2cea-118">Requirements</span></span>  
 <span data-ttu-id="c2cea-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2cea-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2cea-120">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="c2cea-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c2cea-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c2cea-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c2cea-122">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2cea-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cea-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="c2cea-123">See also</span></span>

- [<span data-ttu-id="c2cea-124">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="c2cea-124">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="c2cea-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="c2cea-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="c2cea-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="c2cea-126">Hosting</span></span>](index.md)
