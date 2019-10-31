---
title: Função CorBindToCurrentRuntime
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 77a0a8f58c11673a1958d837b4c3a21a05754c94
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138328"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="dd416-102">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="dd416-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="dd416-103">Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="dd416-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="dd416-104">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="dd416-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="dd416-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="dd416-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="dd416-106">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="dd416-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="dd416-107">Consulte [carregando o Common Language Runtime em um processo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="dd416-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd416-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dd416-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd416-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="dd416-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="dd416-110">no O nome de um arquivo de configuração de aplicativo que especifica a versão do CLR a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="dd416-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="dd416-111">Se o nome do arquivo não for totalmente qualificado, supõe-se que esteja no mesmo diretório que o executável que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="dd416-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="dd416-112">A versão do tempo de execução a ser carregada é descrita pelo atributo Version no elemento [\<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="dd416-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="dd416-113">Se nenhuma versão for especificada ou se o elemento `<requiredRuntime>` não puder ser encontrado, a versão mais recente do CLR instalada no computador será carregada.</span><span class="sxs-lookup"><span data-stu-id="dd416-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="dd416-114">no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="dd416-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="dd416-115">Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="dd416-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="dd416-116">no O `IID` da interface que você está solicitando.</span><span class="sxs-lookup"><span data-stu-id="dd416-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="dd416-117">Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="dd416-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="dd416-118">fora O ponteiro de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="dd416-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd416-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dd416-119">Requirements</span></span>  
 <span data-ttu-id="dd416-120">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd416-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd416-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dd416-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dd416-122">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="dd416-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd416-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd416-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd416-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dd416-124">See also</span></span>

- [<span data-ttu-id="dd416-125">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="dd416-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="dd416-126">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="dd416-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="dd416-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="dd416-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="dd416-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dd416-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="dd416-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="dd416-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="dd416-130">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="dd416-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
