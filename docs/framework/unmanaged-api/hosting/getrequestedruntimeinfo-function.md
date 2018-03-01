---
title: "Função GetRequestedRuntimeInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- GetRequestedRuntimeInfo
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetRequestedRuntimeInfo
helpviewer_keywords:
- GetRequestedRuntimeInfo function [.NET Framework hosting]
ms.assetid: 0dfd7cdc-c116-4e25-b56a-ac7b0378c942
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49459001d3764988eff7b7a4381a843c44e596cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="84619-102">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="84619-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="84619-103">Obtém a versão e informações de diretório sobre o common language runtime (CLR) solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84619-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="84619-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="84619-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84619-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84619-105">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeInfo (  
    [in]  LPCWSTR  pExe,   
    [in]  LPCWSTR  pwszVersion,   
    [in]  LPCWSTR  pConfigurationFile,   
    [in]  DWORD    startupFlags,   
    [in]  DWORD    runtimeInfoFlags,   
    [out] LPWSTR   pDirectory,   
    [in]  DWORD    dwDirectory,   
    [out] DWORD   *dwDirectoryLength,   
    [out] LPWSTR   pVersion,   
    [in]  DWORD    cchBuffer,   
    [out] DWORD   *dwlength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="84619-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84619-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="84619-107">[in] O nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="84619-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="84619-108">[in] Uma cadeia de caracteres que especifica o número de versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="84619-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="84619-109">[in] O nome do arquivo de configuração que está associado com `pExe`.</span><span class="sxs-lookup"><span data-stu-id="84619-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="84619-110">[in] Um ou mais o [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="84619-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="84619-111">[in] Um ou mais o [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="84619-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="84619-112">[out] Um buffer que contém o caminho do diretório no tempo de execução após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="84619-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="84619-113">[in] O comprimento do buffer de diretório.</span><span class="sxs-lookup"><span data-stu-id="84619-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="84619-114">[out] Um ponteiro para o comprimento da cadeia de caracteres de caminho de diretório.</span><span class="sxs-lookup"><span data-stu-id="84619-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="84619-115">[out] Um buffer que contém o número de versão do tempo de execução após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="84619-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="84619-116">[in] O comprimento do buffer de cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="84619-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="84619-117">[out] Um ponteiro para o comprimento da cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="84619-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84619-118">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="84619-118">Return Value</span></span>  
 <span data-ttu-id="84619-119">Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="84619-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="84619-120">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="84619-120">Return code</span></span>|<span data-ttu-id="84619-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="84619-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="84619-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="84619-122">S_OK</span></span>|<span data-ttu-id="84619-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="84619-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="84619-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="84619-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="84619-125">O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="84619-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="84619-126">- ou -</span><span class="sxs-lookup"><span data-stu-id="84619-126">- or -</span></span><br /><br /> <span data-ttu-id="84619-127">O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="84619-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84619-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="84619-128">Remarks</span></span>  
 <span data-ttu-id="84619-129">O `GetRequestedRuntimeInfo` método retorna informações de tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="84619-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="84619-130">No .NET Framework versão 2.0, você pode obter informações sobre a versão mais recente instalada usando o `GetRequestedRuntimeInfo` método da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="84619-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
-   <span data-ttu-id="84619-131">Especifique o `pExe`, `pwszVersion`, e `pConfigurationFile` parâmetros como null.</span><span class="sxs-lookup"><span data-stu-id="84619-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
-   <span data-ttu-id="84619-132">Especifique o sinalizador de RUNTIME_INFO_UPGRADE_VERSION o `RUNTIME_INFO_FLAGS` enumerações para o `runtimeInfoFlags` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84619-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="84619-133">O `GetRequestedRuntimeInfo` método não retorna a versão mais recente do CLR nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="84619-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
-   <span data-ttu-id="84619-134">Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma versão específica do CLR.</span><span class="sxs-lookup"><span data-stu-id="84619-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="84619-135">Observe que o .NET Framework usará o arquivo de configuração, mesmo se você especificar null para o `pConfigurationFile` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84619-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
-   <span data-ttu-id="84619-136">O [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) método foi chamado para especificar uma versão anterior do CLR.</span><span class="sxs-lookup"><span data-stu-id="84619-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
-   <span data-ttu-id="84619-137">Um aplicativo que foi compilado para uma versão anterior do CLR está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="84619-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="84619-138">Para o `runtimeInfoFlags` parâmetro, você pode especificar apenas uma das constantes de arquitetura do `RUNTIME_INFO_FLAGS` enumeração por vez:</span><span class="sxs-lookup"><span data-stu-id="84619-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
-   <span data-ttu-id="84619-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="84619-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="84619-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="84619-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="84619-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="84619-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84619-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84619-142">Requirements</span></span>  
 <span data-ttu-id="84619-143">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84619-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84619-144">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="84619-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="84619-145">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="84619-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="84619-146">**Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84619-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84619-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84619-147">See Also</span></span>  
 [<span data-ttu-id="84619-148">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="84619-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
 [<span data-ttu-id="84619-149">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="84619-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="84619-150">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="84619-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
