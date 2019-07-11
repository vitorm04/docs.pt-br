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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 505bba3bb5d08c13e29543c20df2daaebc863d12
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768011"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="0e664-102">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="0e664-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="0e664-103">Carrega o common language runtime (CLR) em um processo usando informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="0e664-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="0e664-104">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="0e664-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="0e664-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="0e664-105">For more information about configuration files, see [Configuration File Schema](../../../../docs/framework/configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="0e664-106">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0e664-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="0e664-107">Ver [carregando o Common Language Runtime em um processo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0e664-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e664-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e664-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e664-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e664-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="0e664-110">[in] O nome de um arquivo de configuração de aplicativo que especifica a versão do CLR para carregar.</span><span class="sxs-lookup"><span data-stu-id="0e664-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="0e664-111">Se o nome do arquivo não é totalmente qualificado, será considerado estar no mesmo diretório que o executável que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="0e664-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="0e664-112">A versão do tempo de execução a ser carregado é descrita pelo atributo na versão de [ \<requiredRuntime >](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0e664-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="0e664-113">Se nenhuma versão for especificada, ou se o `<requiredRuntime>` elemento não pode ser encontrado, a versão mais recente do CLR que está instalado na máquina é carregada.</span><span class="sxs-lookup"><span data-stu-id="0e664-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="0e664-114">[in] O `CLSID` da coclass que implementa o [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ou o [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="0e664-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) or the [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="0e664-115">Valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0e664-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="0e664-116">[in] O `IID` da interface que você está solicitando.</span><span class="sxs-lookup"><span data-stu-id="0e664-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="0e664-117">Valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="0e664-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="0e664-118">[out] O ponteiro de interface retornada.</span><span class="sxs-lookup"><span data-stu-id="0e664-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e664-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e664-119">Requirements</span></span>  
 <span data-ttu-id="0e664-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e664-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e664-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0e664-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e664-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e664-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e664-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e664-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e664-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e664-124">See also</span></span>

- [<span data-ttu-id="0e664-125">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="0e664-125">CorBindToRuntime Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [<span data-ttu-id="0e664-126">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="0e664-126">CorBindToRuntimeByCfg Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="0e664-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="0e664-127">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="0e664-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e664-128">CorBindToRuntimeHost Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [<span data-ttu-id="0e664-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="0e664-129">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [<span data-ttu-id="0e664-130">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="0e664-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
