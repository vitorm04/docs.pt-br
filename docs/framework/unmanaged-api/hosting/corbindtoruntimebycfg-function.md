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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbba208296dd2099c9da58c81ff66fddc78fdc86
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985862"
---
# <a name="corbindtoruntimebycfg-function"></a><span data-ttu-id="9b76b-102">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="9b76b-102">CorBindToRuntimeByCfg Function</span></span>
<span data-ttu-id="9b76b-103">Carrega o common language runtime (CLR) em um processo usando informações de versão que é lido de um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="9b76b-103">Loads the common language runtime (CLR) into a process by using version information that is read from an XML file.</span></span>  
  
 <span data-ttu-id="9b76b-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9b76b-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b76b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9b76b-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="9b76b-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9b76b-106">Parameters</span></span>  
 `pCfgStream`  
 <span data-ttu-id="9b76b-107">[in] Um ponteiro para um `IStream` objeto que lê o arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="9b76b-107">[in] A pointer to an `IStream` object that reads the XML file.</span></span>  
  
 `reserved`  
 <span data-ttu-id="9b76b-108">[in] Reservado para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="9b76b-108">[in] Reserved for future use.</span></span> <span data-ttu-id="9b76b-109">Use 0 (zero) como valor.</span><span class="sxs-lookup"><span data-stu-id="9b76b-109">Use 0 (zero) as value.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="9b76b-110">[in] Um valor igual a [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeração que especifica o comportamento de inicialização do CLR.</span><span class="sxs-lookup"><span data-stu-id="9b76b-110">[in] A value of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration that specifies the startup behavior of the CLR.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="9b76b-111">[in] O `CLSID` da coclass que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="9b76b-111">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="9b76b-112">Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9b76b-112">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="9b76b-113">[in] O `IID` de um a `ICorRuntimeHost` ou o `ICLRRuntimeHost` interface.</span><span class="sxs-lookup"><span data-stu-id="9b76b-113">[in] The `IID` of either the `ICorRuntimeHost` or the `ICLRRuntimeHost` interface.</span></span> <span data-ttu-id="9b76b-114">Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="9b76b-114">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="9b76b-115">[out] Um ponteiro para o endereço da interface retornada.</span><span class="sxs-lookup"><span data-stu-id="9b76b-115">[out] A pointer to the address of the returned interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b76b-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="9b76b-116">Remarks</span></span>  
 <span data-ttu-id="9b76b-117">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="9b76b-117">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="9b76b-118">Para obter mais informações sobre os arquivos XML, consulte [esquema de arquivo de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b76b-118">For more information about XML files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b76b-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9b76b-119">Requirements</span></span>  
 <span data-ttu-id="9b76b-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b76b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b76b-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9b76b-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9b76b-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9b76b-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9b76b-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b76b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b76b-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9b76b-124">See also</span></span>

- [<span data-ttu-id="9b76b-125">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="9b76b-125">CorBindToCurrentRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [<span data-ttu-id="9b76b-126">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="9b76b-126">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="9b76b-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="9b76b-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="9b76b-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9b76b-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="9b76b-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="9b76b-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="9b76b-130">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="9b76b-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
