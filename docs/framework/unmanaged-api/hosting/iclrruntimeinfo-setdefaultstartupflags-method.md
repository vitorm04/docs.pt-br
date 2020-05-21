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
ms.openlocfilehash: 7d201962976d198372226eb686696fcdccf3eb69
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762156"
---
# <a name="iclrruntimeinfosetdefaultstartupflags-method"></a><span data-ttu-id="556f7-102">Método ICLRRuntimeInfo::SetDefaultStartupFlags</span><span class="sxs-lookup"><span data-stu-id="556f7-102">ICLRRuntimeInfo::SetDefaultStartupFlags Method</span></span>
<span data-ttu-id="556f7-103">Define os sinalizadores de inicialização e o arquivo de configuração do host que será usado para iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="556f7-103">Sets the startup flags and the host configuration file that will be used to start the runtime.</span></span> <span data-ttu-id="556f7-104">Esse método substitui o uso do `startupFlags` parâmetro nas funções [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="556f7-104">This method supersedes the use of the `startupFlags` parameter in the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="556f7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="556f7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetDefaultStartupFlags(  
           [in]  DWORD dwStartupFlags,  
           [in]  LPCWSTR pwzHostConfigFile);  
```  
  
## <a name="parameters"></a><span data-ttu-id="556f7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="556f7-106">Parameters</span></span>  
 `dwStartupFlags`  
 <span data-ttu-id="556f7-107">no Os sinalizadores de inicialização do host a serem definidos.</span><span class="sxs-lookup"><span data-stu-id="556f7-107">[in] The host startup flags to set.</span></span> <span data-ttu-id="556f7-108">Use os mesmos sinalizadores que as funções [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) e [CorBindToRuntimeHost](corbindtoruntimehost-function.md) .</span><span class="sxs-lookup"><span data-stu-id="556f7-108">Use the same flags as with the [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) and [CorBindToRuntimeHost](corbindtoruntimehost-function.md) functions.</span></span>  
  
 `pwzHostConfigFile`  
 <span data-ttu-id="556f7-109">no O caminho do diretório do arquivo de configuração do host a ser definido.</span><span class="sxs-lookup"><span data-stu-id="556f7-109">[in] The directory path of the host configuration file to set.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="556f7-110">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="556f7-110">Return Value</span></span>  
 <span data-ttu-id="556f7-111">Esse método retorna o HRESULT específico a seguir, bem como erros HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="556f7-111">This method returns the following specific HRESULT as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="556f7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="556f7-112">HRESULT</span></span>|<span data-ttu-id="556f7-113">Description</span><span class="sxs-lookup"><span data-stu-id="556f7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="556f7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="556f7-114">S_OK</span></span>|<span data-ttu-id="556f7-115">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="556f7-115">The method completed successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="556f7-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="556f7-116">Remarks</span></span>  
 <span data-ttu-id="556f7-117">Um host multi-threaded deve sincronizar chamadas para esse método.</span><span class="sxs-lookup"><span data-stu-id="556f7-117">A multithreaded host should synchronize calls to this method.</span></span> <span data-ttu-id="556f7-118">Caso contrário, o thread A pode chamar o `SetStartupFlags` método depois que o thread b concluir uma chamada para `SetStartupFlags` e antes do thread b iniciar o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="556f7-118">Otherwise, thread A might call the `SetStartupFlags` method after thread B completes a call to `SetStartupFlags` and before thread B starts the runtime.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="556f7-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="556f7-119">Requirements</span></span>  
 <span data-ttu-id="556f7-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="556f7-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="556f7-121">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="556f7-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="556f7-122">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="556f7-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="556f7-123">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="556f7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="556f7-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="556f7-124">See also</span></span>

- [<span data-ttu-id="556f7-125">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="556f7-125">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="556f7-126">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="556f7-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="556f7-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="556f7-127">Hosting</span></span>](index.md)
