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
ms.openlocfilehash: 2996acd9678557b08fcfa543ecc7648ed639b143
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748333"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="2d5a4-102">Método ICLRRuntimeInfo::SetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="2d5a4-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="2d5a4-103">Define os sinalizadores de inicialização e o arquivo de configuração de host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="2d5a4-104">Esse método substitui o uso do `startupFlags` parâmetro na [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d5a4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2d5a4-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2d5a4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2d5a4-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="2d5a4-107">[in] Os sinalizadores de inicialização do host para definir.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="2d5a4-108">Use os mesmos sinalizadores como com o [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) funções.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="2d5a4-109">[in] O caminho do diretório do arquivo de configuração de host para definir.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d5a4-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="2d5a4-110">Return Value</span></span>  
 <span data-ttu-id="2d5a4-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha do método.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="2d5a4-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d5a4-112">HRESULT</span></span>|<span data-ttu-id="2d5a4-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2d5a4-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d5a4-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d5a4-114">S_OK</span></span>|<span data-ttu-id="2d5a4-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d5a4-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="2d5a4-116">Remarks</span></span>  
 <span data-ttu-id="2d5a4-117">Um host de vários threads deve sincronizar chamadas para esse método.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="2d5a4-118">Caso contrário, o thread A pode chamar o `SetStartupFlags` método depois que o thread B conclui uma chamada para `SetStartupFlags` e antes do thread B se inicia o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="2d5a4-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d5a4-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2d5a4-119">Requirements</span></span>  
 <span data-ttu-id="2d5a4-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d5a4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d5a4-121">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="2d5a4-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2d5a4-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2d5a4-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d5a4-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d5a4-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d5a4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d5a4-124">See also</span></span>

- [<span data-ttu-id="2d5a4-125">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="2d5a4-125">ICLRRuntimeInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)
- [<span data-ttu-id="2d5a4-126">Hospedagem de Interfaces</span><span class="sxs-lookup"><span data-stu-id="2d5a4-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="2d5a4-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="2d5a4-127">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
