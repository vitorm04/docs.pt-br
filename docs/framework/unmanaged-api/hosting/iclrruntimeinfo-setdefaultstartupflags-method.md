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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3174cf3b4f4f4ac4b2c8e69030357eb1e46cf3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197822"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="e09ad-102">Método ICLRRuntimeInfo::SetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="e09ad-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="e09ad-103">Define os sinalizadores de inicialização e o arquivo de configuração de host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e09ad-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="e09ad-104">Esse método substitui o uso do `startupFlags` parâmetro na [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="e09ad-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e09ad-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e09ad-105">Syntax</span></span>  
  
```  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e09ad-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e09ad-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="e09ad-107">[in] Os sinalizadores de inicialização do host para definir.</span><span class="sxs-lookup"><span data-stu-id="e09ad-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="e09ad-108">Use os mesmos sinalizadores como com o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="e09ad-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="e09ad-109">[in] O caminho do diretório do arquivo de configuração de host para definir.</span><span class="sxs-lookup"><span data-stu-id="e09ad-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e09ad-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e09ad-110">Return Value</span></span>  
 <span data-ttu-id="e09ad-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="e09ad-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="e09ad-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e09ad-112">HRESULT</span></span>|<span data-ttu-id="e09ad-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="e09ad-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e09ad-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="e09ad-114">S_OK</span></span>|<span data-ttu-id="e09ad-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="e09ad-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e09ad-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="e09ad-116">Remarks</span></span>  
 <span data-ttu-id="e09ad-117">Um host de vários threads deve sincronizar chamadas para esse método.</span><span class="sxs-lookup"><span data-stu-id="e09ad-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="e09ad-118">Caso contrário, o thread A pode chamar o `SetStartupFlags` método depois que o thread B conclui uma chamada para `SetStartupFlags` e antes do thread B se inicia o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e09ad-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e09ad-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e09ad-119">Requirements</span></span>  
 <span data-ttu-id="e09ad-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e09ad-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e09ad-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="e09ad-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="e09ad-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="e09ad-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e09ad-123">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e09ad-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e09ad-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e09ad-124">See also</span></span>

- [<span data-ttu-id="e09ad-125">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="e09ad-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="e09ad-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="e09ad-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="e09ad-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="e09ad-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
