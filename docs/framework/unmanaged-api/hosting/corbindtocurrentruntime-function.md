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
ms.openlocfilehash: 4c015d77deb4e6ed3d43074f2903e26b687de84f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493559"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="a10f8-102">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="a10f8-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="a10f8-103">Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="a10f8-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="a10f8-104">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="a10f8-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="a10f8-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="a10f8-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="a10f8-106">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a10f8-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="a10f8-107">Consulte [carregando o Common Language Runtime em um processo](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a10f8-107">See [Loading the Common Language Runtime into a Process](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a10f8-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a10f8-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a10f8-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a10f8-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="a10f8-110">no O nome de um arquivo de configuração de aplicativo que especifica a versão do CLR a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="a10f8-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="a10f8-111">Se o nome do arquivo não for totalmente qualificado, supõe-se que esteja no mesmo diretório que o executável que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="a10f8-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="a10f8-112">A versão do tempo de execução a ser carregada é descrita pelo atributo Version no [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="a10f8-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="a10f8-113">Se nenhuma versão for especificada ou se o `<requiredRuntime>` elemento não puder ser encontrado, a versão mais recente do CLR instalada no computador será carregada.</span><span class="sxs-lookup"><span data-stu-id="a10f8-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="a10f8-114">no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a10f8-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="a10f8-115">Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a10f8-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="a10f8-116">no O `IID` da interface que você está solicitando.</span><span class="sxs-lookup"><span data-stu-id="a10f8-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="a10f8-117">Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="a10f8-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="a10f8-118">fora O ponteiro de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="a10f8-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a10f8-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a10f8-119">Requirements</span></span>  
 <span data-ttu-id="a10f8-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a10f8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a10f8-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a10f8-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a10f8-122">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a10f8-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a10f8-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a10f8-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10f8-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="a10f8-124">See also</span></span>

- [<span data-ttu-id="a10f8-125">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="a10f8-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="a10f8-126">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="a10f8-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="a10f8-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="a10f8-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="a10f8-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a10f8-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="a10f8-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="a10f8-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="a10f8-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="a10f8-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
