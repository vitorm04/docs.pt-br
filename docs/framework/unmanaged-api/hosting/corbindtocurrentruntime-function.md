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
ms.openlocfilehash: 9c5d83b5f2ffb06c9fb14f715a3ea7ff12319086
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547807"
---
# <a name="corbindtocurrentruntime-function"></a><span data-ttu-id="17c60-102">Função CorBindToCurrentRuntime</span><span class="sxs-lookup"><span data-stu-id="17c60-102">CorBindToCurrentRuntime Function</span></span>
<span data-ttu-id="17c60-103">Carrega o Common Language Runtime (CLR) em um processo usando as informações de versão armazenadas em um arquivo XML.</span><span class="sxs-lookup"><span data-stu-id="17c60-103">Loads the common language runtime (CLR) into a process by using version information stored in an XML file.</span></span> <span data-ttu-id="17c60-104">O formato do arquivo XML é modelado após o arquivo de configuração de aplicativo padrão.</span><span class="sxs-lookup"><span data-stu-id="17c60-104">The format of the XML file is modeled after the standard application configuration file.</span></span> <span data-ttu-id="17c60-105">Para obter mais informações sobre arquivos de configuração, consulte [Esquema de arquivos de configuração](../../configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="17c60-105">For more information about configuration files, see [Configuration File Schema](../../configure-apps/file-schema/index.md).</span></span>  
  
 <span data-ttu-id="17c60-106">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="17c60-106">This function has been deprecated in the .NET Framework 4.</span></span> <span data-ttu-id="17c60-107">Consulte [carregando o Common Language Runtime em um processo](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="17c60-107">See [Loading the Common Language Runtime into a Process](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17c60-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17c60-108">Syntax</span></span>  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17c60-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17c60-109">Parameters</span></span>  
 `pwszFileName`  
 <span data-ttu-id="17c60-110">no O nome de um arquivo de configuração de aplicativo que especifica a versão do CLR a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="17c60-110">[in] The name of an application configuration file that specifies the version of the CLR to load.</span></span> <span data-ttu-id="17c60-111">Se o nome do arquivo não for totalmente qualificado, supõe-se que esteja no mesmo diretório que o executável que faz a chamada.</span><span class="sxs-lookup"><span data-stu-id="17c60-111">If the file name is not fully qualified, it is assumed to be in the same directory as the executable making the call.</span></span>  
  
 <span data-ttu-id="17c60-112">A versão do tempo de execução a ser carregada é descrita pelo atributo Version no [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) elemento do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="17c60-112">The version of the runtime to be loaded is described by the version attribute in the [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) element of the configuration file.</span></span>  
  
 <span data-ttu-id="17c60-113">Se nenhuma versão for especificada ou se o `<requiredRuntime>` elemento não puder ser encontrado, a versão mais recente do CLR instalada no computador será carregada.</span><span class="sxs-lookup"><span data-stu-id="17c60-113">If no version is specified, or if the `<requiredRuntime>` element cannot be found, the latest version of the CLR that is installed on the machine is loaded.</span></span>  
  
 `rclsid`  
 <span data-ttu-id="17c60-114">no O `CLSID` da coclass que implementa a interface [ICorRuntimeHost](icorruntimehost-interface.md) ou [ICLRRuntimeHost](iclrruntimehost-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="17c60-114">[in] The `CLSID` of the coclass that implements either the [ICorRuntimeHost](icorruntimehost-interface.md) or the [ICLRRuntimeHost](iclrruntimehost-interface.md) interface.</span></span> <span data-ttu-id="17c60-115">Os valores com suporte são CLSID_CorRuntimeHost ou CLSID_CLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="17c60-115">Supported values are CLSID_CorRuntimeHost or CLSID_CLRRuntimeHost.</span></span>  
  
 `riid`  
 <span data-ttu-id="17c60-116">no O `IID` da interface que você está solicitando.</span><span class="sxs-lookup"><span data-stu-id="17c60-116">[in] The `IID` of the interface you are requesting.</span></span> <span data-ttu-id="17c60-117">Os valores com suporte são IID_ICorRuntimeHost ou IID_ICLRRuntimeHost.</span><span class="sxs-lookup"><span data-stu-id="17c60-117">Supported values are IID_ICorRuntimeHost or IID_ICLRRuntimeHost.</span></span>  
  
 `ppv`  
 <span data-ttu-id="17c60-118">fora O ponteiro de interface retornado.</span><span class="sxs-lookup"><span data-stu-id="17c60-118">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17c60-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17c60-119">Requirements</span></span>  
 <span data-ttu-id="17c60-120">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17c60-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17c60-121">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17c60-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17c60-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17c60-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17c60-123">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17c60-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17c60-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="17c60-124">See also</span></span>

- [<span data-ttu-id="17c60-125">Função CorBindToRuntime</span><span class="sxs-lookup"><span data-stu-id="17c60-125">CorBindToRuntime Function</span></span>](corbindtoruntime-function.md)
- [<span data-ttu-id="17c60-126">Função CorBindToRuntimeByCfg</span><span class="sxs-lookup"><span data-stu-id="17c60-126">CorBindToRuntimeByCfg Function</span></span>](corbindtoruntimebycfg-function.md)
- [<span data-ttu-id="17c60-127">Função CorBindToRuntimeEx</span><span class="sxs-lookup"><span data-stu-id="17c60-127">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="17c60-128">Função CorBindToRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="17c60-128">CorBindToRuntimeHost Function</span></span>](corbindtoruntimehost-function.md)
- [<span data-ttu-id="17c60-129">Interface ICorRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="17c60-129">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="17c60-130">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="17c60-130">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
