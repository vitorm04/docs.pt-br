---
title: Função GetRequestedRuntimeInfo
ms.date: 03/30/2017
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
ms.openlocfilehash: db721e1ef774c87de0fa7da178463d832a3da756
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178147"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="7ec8d-102">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="7ec8d-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="7ec8d-103">Obtém informações de versão e diretório sobre o tempo de execução do idioma comum (CLR) solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="7ec8d-104">Esta função foi depreciada no Quadro .NET 4.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec8d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ec8d-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="7ec8d-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ec8d-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="7ec8d-107">[em] O nome da aplicação.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="7ec8d-108">[em] Uma seqüência especificando o número da versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="7ec8d-109">[em] O nome do arquivo de `pExe`configuração que está associado a .</span><span class="sxs-lookup"><span data-stu-id="7ec8d-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="7ec8d-110">[em] Um ou mais dos valores [de enumeração STARTUP_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="7ec8d-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="7ec8d-111">[em] Um ou mais dos valores de enumeração [RUNTIME_INFO_FLAGS.](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="7ec8d-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="7ec8d-112">[fora] Um buffer que contém o caminho do diretório para o tempo de execução após a conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="7ec8d-113">[em] A duração do buffer do diretório.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="7ec8d-114">[fora] Um ponteiro para o comprimento da seqüência do caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="7ec8d-115">[fora] Um buffer que contém o número da versão do tempo de execução após a conclusão bem sucedida.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7ec8d-116">[em] O comprimento do buffer de string da versão.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="7ec8d-117">[fora] Um ponteiro para o comprimento da seqüência de versão.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7ec8d-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7ec8d-118">Return Value</span></span>  
 <span data-ttu-id="7ec8d-119">Este método retorna códigos de erro com (Component Object Model, modelo de objeto componente padrão), conforme definido em WinError.h, além dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="7ec8d-120">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="7ec8d-120">Return code</span></span>|<span data-ttu-id="7ec8d-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ec8d-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="7ec8d-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="7ec8d-122">S_OK</span></span>|<span data-ttu-id="7ec8d-123">O método foi concluído com sucesso.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="7ec8d-124">Error_insufficient_buffer</span><span class="sxs-lookup"><span data-stu-id="7ec8d-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="7ec8d-125">O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="7ec8d-126">- ou -</span><span class="sxs-lookup"><span data-stu-id="7ec8d-126">- or -</span></span><br /><br /> <span data-ttu-id="7ec8d-127">O buffer de versão não é grande o suficiente para armazenar a seqüência de versões.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ec8d-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ec8d-128">Remarks</span></span>  
 <span data-ttu-id="7ec8d-129">O `GetRequestedRuntimeInfo` método retorna informações em tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="7ec8d-130">Na versão 2.0 do .NET Framework, você pode obter informações `GetRequestedRuntimeInfo` sobre a versão instalada mais recente usando o método da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="7ec8d-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="7ec8d-131">Especifique os `pExe` `pwszVersion`parâmetros e `pConfigurationFile` os parâmetros como nulos.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="7ec8d-132">Especifique a `RUNTIME_INFO_FLAGS` bandeira RUNTIME_INFO_UPGRADE_VERSION `runtimeInfoFlags` nas enumerações para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="7ec8d-133">O `GetRequestedRuntimeInfo` método não retorna a versão CLR mais recente nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="7ec8d-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="7ec8d-134">Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma determinada versão CLR.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="7ec8d-135">Observe que o .NET Framework usará o arquivo de `pConfigurationFile` configuração mesmo se você especificar nulo para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="7ec8d-136">O método [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) foi chamado especificando uma versão CLR anterior.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="7ec8d-137">Um aplicativo que foi compilado para uma versão CLR anterior está atualmente em execução.</span><span class="sxs-lookup"><span data-stu-id="7ec8d-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="7ec8d-138">Para `runtimeInfoFlags` o parâmetro, você pode especificar apenas uma `RUNTIME_INFO_FLAGS` das constantes de arquitetura da enumeração de cada vez:</span><span class="sxs-lookup"><span data-stu-id="7ec8d-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="7ec8d-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="7ec8d-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="7ec8d-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="7ec8d-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="7ec8d-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="7ec8d-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ec8d-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ec8d-142">Requirements</span></span>  
 <span data-ttu-id="7ec8d-143">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec8d-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec8d-144">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7ec8d-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7ec8d-145">**Biblioteca:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7ec8d-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7ec8d-146">**.NET Framework Versions:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec8d-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec8d-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="7ec8d-147">See also</span></span>

- [<span data-ttu-id="7ec8d-148">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="7ec8d-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="7ec8d-149">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="7ec8d-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="7ec8d-150">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="7ec8d-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
