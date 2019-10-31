---
title: Método ICLRRuntimeInfo::SetDefaultStartupFlags
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.SetDefaultStartupFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type:
- apiref
ms.openlocfilehash: 36851ac4573d0d65caffaa3f82a1f6fc8440a2d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092747"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="f0916-102">Método ICLRRuntimeInfo::SetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="f0916-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="f0916-103">Define os sinalizadores de inicialização e o arquivo de configuração do host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f0916-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="f0916-104">Esse método substitui o uso do parâmetro `startupFlags` nas funções [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f0916-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0916-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0916-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0916-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0916-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="f0916-107">no Os sinalizadores de inicialização do host a serem definidos.</span><span class="sxs-lookup"><span data-stu-id="f0916-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="f0916-108">Use os mesmos sinalizadores que as funções [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="f0916-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="f0916-109">no O caminho do diretório do arquivo de configuração do host a ser definido.</span><span class="sxs-lookup"><span data-stu-id="f0916-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0916-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f0916-110">Return Value</span></span>  
 <span data-ttu-id="f0916-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="f0916-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f0916-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f0916-112">HRESULT</span></span>|<span data-ttu-id="f0916-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="f0916-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f0916-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="f0916-114">S_OK</span></span>|<span data-ttu-id="f0916-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f0916-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0916-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="f0916-116">Remarks</span></span>  
 <span data-ttu-id="f0916-117">Um host multi-threaded deve sincronizar chamadas para esse método.</span><span class="sxs-lookup"><span data-stu-id="f0916-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="f0916-118">Caso contrário, o thread A pode chamar o método `SetStartupFlags` depois que o thread B concluir uma chamada para `SetStartupFlags` e antes do thread B iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="f0916-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0916-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0916-119">Requirements</span></span>  
 <span data-ttu-id="f0916-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0916-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0916-121">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="f0916-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f0916-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f0916-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f0916-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0916-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0916-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0916-124">See also</span></span>

- [<span data-ttu-id="f0916-125">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="f0916-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="f0916-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="f0916-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="f0916-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="f0916-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
