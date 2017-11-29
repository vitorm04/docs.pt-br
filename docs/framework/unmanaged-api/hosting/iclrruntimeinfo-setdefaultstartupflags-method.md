---
title: "Método ICLRRuntimeInfo::SetDefaultStartupFlags"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo.SetDefaultStartupFlags
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo::SetDefaultStartupFlags
helpviewer_keywords:
- ICLRRuntimeInfo::SetDefaultStartupFlags method [.NET Framework hosting]
- SetDefaultStartupFlags method [.NET Framework hosting]
ms.assetid: 98ae174f-bff0-48f1-9e05-6cb63b451824
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1732073b9799453bd32447e7a688b0280e66f1ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="a0921-102">Método ICLRRuntimeInfo::SetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="a0921-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="a0921-103">Define os sinalizadores de inicialização e o arquivo de configuração de host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0921-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="a0921-104">Esse método substitui o uso do `startupFlags` parâmetro o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="a0921-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0921-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0921-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a0921-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a0921-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="a0921-107">[in] Os sinalizadores de inicialização de host definido.</span><span class="sxs-lookup"><span data-stu-id="a0921-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="a0921-108">Use os mesmos sinalizadores como com o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="a0921-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="a0921-109">[in] O caminho do diretório do arquivo de configuração de host para definir.</span><span class="sxs-lookup"><span data-stu-id="a0921-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0921-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a0921-110">Return Value</span></span>  
 <span data-ttu-id="a0921-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="a0921-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a0921-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0921-112">HRESULT</span></span>|<span data-ttu-id="a0921-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0921-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0921-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0921-114">S_OK</span></span>|<span data-ttu-id="a0921-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a0921-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0921-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a0921-116">Remarks</span></span>  
 <span data-ttu-id="a0921-117">Um host multi-threaded deve sincronizar chamadas para esse método.</span><span class="sxs-lookup"><span data-stu-id="a0921-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="a0921-118">Caso contrário, o thread A pode chamar o `SetStartupFlags` método após uma chamada para conclusão da thread B `SetStartupFlags` e antes do thread B inicia o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0921-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0921-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0921-119">Requirements</span></span>  
 <span data-ttu-id="a0921-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0921-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0921-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="a0921-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="a0921-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a0921-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a0921-123">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0921-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0921-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0921-124">See Also</span></span>  
 [<span data-ttu-id="a0921-125">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a0921-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 [<span data-ttu-id="a0921-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="a0921-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="a0921-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a0921-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
