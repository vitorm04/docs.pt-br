---
title: "Função CorBindToRuntimeByCfg"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntimeByCfg
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CorBindToRuntimeByCfg
helpviewer_keywords: CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bbf5a486246d1fb596c08f1510e6d5d89b03df62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="c7c94-102">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="c7c94-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="c7c94-103">Carrega o common language runtime (CLR) em um processo usando as informações de versão que é lido de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="c7c94-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="c7c94-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c7c94-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7c94-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c7c94-105">Syntax</span></span>  
  
```  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,   
    [out] LPVOID FAR*  ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c7c94-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c7c94-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="c7c94-107">[in] Um ponteiro para um `IStream` objeto que lê o arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="c7c94-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="c7c94-108">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="c7c94-108">[in] Reserved for future use.</span></span> <span data-ttu-id="c7c94-109">Use 0 (zero) como valor.</span><span class="sxs-lookup"><span data-stu-id="c7c94-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="c7c94-110">[in] Um valor de [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração que especifica o comportamento de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="c7c94-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="c7c94-111">[in] O `CLSID` da coclass que implemente tanto o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="c7c94-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="c7c94-112">Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c7c94-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="c7c94-113">[in] O `IID` da `ICorRuntimeHost` ou `ICLRRuntimeHost` interface.</span><span class="sxs-lookup"><span data-stu-id="c7c94-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="c7c94-114">Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="c7c94-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="c7c94-115">[out] Um ponteiro para o endereço da interface retornado.</span><span class="sxs-lookup"><span data-stu-id="c7c94-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7c94-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="c7c94-116">Remarks</span></span>  
 <span data-ttu-id="c7c94-117">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="c7c94-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="c7c94-118">Para obter mais informações sobre os arquivos XML, consulte [esquema de arquivo de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="c7c94-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7c94-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c7c94-119">Requirements</span></span>  
 <span data-ttu-id="c7c94-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7c94-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7c94-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7c94-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7c94-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c7c94-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7c94-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7c94-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7c94-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7c94-124">See Also</span></span>  
 [<span data-ttu-id="c7c94-125">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="c7c94-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [<span data-ttu-id="c7c94-126">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="c7c94-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [<span data-ttu-id="c7c94-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="c7c94-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="c7c94-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c7c94-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [<span data-ttu-id="c7c94-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c7c94-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [<span data-ttu-id="c7c94-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="c7c94-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
