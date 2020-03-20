---
title: Função CorBindToRuntimeByCfg
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: 4fbc6e7ea531f65a6b1cd0ec93f4847ab8e4fe83
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178239"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="9e318-102">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="9e318-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="9e318-103">Carrega o tempo de execução do idioma comum (CLR) em um processo usando informações de versão que são lidas a partir de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="9e318-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="9e318-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="9e318-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e318-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9e318-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e318-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9e318-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="9e318-107">[em] Um ponteiro `IStream` para um objeto que lê o arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="9e318-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="9e318-108">[em] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="9e318-108">[in] Reserved for future use.</span></span> <span data-ttu-id="9e318-109">Use 0 (zero) como valor.</span><span class="sxs-lookup"><span data-stu-id="9e318-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="9e318-110">[em] Um valor da [enumeração STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) que especifica o comportamento de inicialização da CLR.</span><span class="sxs-lookup"><span data-stu-id="9e318-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9e318-111">[em] A `CLSID` coclasse que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou a interface [ICLRRuntimeHost.](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)</span><span class="sxs-lookup"><span data-stu-id="9e318-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9e318-112">Os valores suportados são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9e318-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9e318-113">[em] O `IID` da `ICorRuntimeHost` interface `ICLRRuntimeHost` ou da interface.</span><span class="sxs-lookup"><span data-stu-id="9e318-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="9e318-114">Os valores suportados são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9e318-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9e318-115">[fora] Um ponteiro para o endereço da interface retornada.</span><span class="sxs-lookup"><span data-stu-id="9e318-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e318-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="9e318-116">Remarks</span></span>  
 <span data-ttu-id="9e318-117">O formato do arquivo XML é modelado após o arquivo de configuração padrão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9e318-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="9e318-118">Para obter mais informações sobre arquivos XML, consulte [Esquema de arquivo de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e318-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e318-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9e318-119">Requirements</span></span>  
 <span data-ttu-id="9e318-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e318-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e318-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9e318-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e318-122">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="9e318-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e318-123">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e318-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e318-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e318-124">See also</span></span>

- [<span data-ttu-id="9e318-125">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="9e318-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9e318-126">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="9e318-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="9e318-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="9e318-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9e318-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9e318-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9e318-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9e318-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9e318-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="9e318-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
