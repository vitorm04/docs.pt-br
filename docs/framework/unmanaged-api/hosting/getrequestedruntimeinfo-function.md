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
ms.openlocfilehash: cd1d9e768698115bee22e35699b044e0c3526d2d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136320"
---
# <a name="getrequestedruntimeinfo-function"></a><span data-ttu-id="a793a-102">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="a793a-102">GetRequestedRuntimeInfo Function</span></span>
<span data-ttu-id="a793a-103">Obtém informações de versão e diretório sobre o Common Language Runtime (CLR) solicitado por um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a793a-103">Gets version and directory information about the common language runtime (CLR) requested by an application.</span></span>  
  
 <span data-ttu-id="a793a-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a793a-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a793a-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a793a-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a793a-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a793a-106">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="a793a-107">no O nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a793a-107">[in] The name of the application.</span></span>  
  
 `pwszVersion`  
 <span data-ttu-id="a793a-108">no Uma cadeia de caracteres que especifica o número de versão do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a793a-108">[in] A string specifying the version number of the runtime.</span></span>  
  
 `pConfigurationFile`  
 <span data-ttu-id="a793a-109">no O nome do arquivo de configuração associado a `pExe`.</span><span class="sxs-lookup"><span data-stu-id="a793a-109">[in] The name of the configuration file that is associated with `pExe`.</span></span>  
  
 `startupFlags`  
 <span data-ttu-id="a793a-110">no Um ou mais dos valores de enumeração [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a793a-110">[in] One or more of the [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md) enumeration values.</span></span>  
  
 `runtimeInfoFlags`  
 <span data-ttu-id="a793a-111">no Um ou mais dos valores de enumeração [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="a793a-111">[in] One or more of the [RUNTIME_INFO_FLAGS](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md) enumeration values.</span></span>  
  
 `pDirectory`  
 <span data-ttu-id="a793a-112">fora Um buffer que contém o caminho do diretório para o tempo de execução após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a793a-112">[out] A buffer that contains the directory path to the runtime upon successful completion.</span></span>  
  
 `dwDirectory`  
 <span data-ttu-id="a793a-113">no O comprimento do buffer de diretório.</span><span class="sxs-lookup"><span data-stu-id="a793a-113">[in] The length of the directory buffer.</span></span>  
  
 `dwDirectoryLength`  
 <span data-ttu-id="a793a-114">fora Um ponteiro para o comprimento da cadeia de caracteres do caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="a793a-114">[out] A pointer to the length of the directory path string.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="a793a-115">fora Um buffer que contém o número de versão do tempo de execução após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a793a-115">[out] A buffer that contains the version number of the runtime upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="a793a-116">no O comprimento do buffer de cadeia de caracteres da versão.</span><span class="sxs-lookup"><span data-stu-id="a793a-116">[in] The length of the version string buffer.</span></span>  
  
 `dwlength`  
 <span data-ttu-id="a793a-117">fora Um ponteiro para o comprimento da cadeia de caracteres da versão.</span><span class="sxs-lookup"><span data-stu-id="a793a-117">[out] A pointer to the length of the version string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a793a-118">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a793a-118">Return Value</span></span>  
 <span data-ttu-id="a793a-119">Esse método retorna códigos de erro padrão de Component Object Model (COM), conforme definido no WinError. h, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="a793a-119">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a793a-120">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="a793a-120">Return code</span></span>|<span data-ttu-id="a793a-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="a793a-121">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a793a-122">S_OK</span><span class="sxs-lookup"><span data-stu-id="a793a-122">S_OK</span></span>|<span data-ttu-id="a793a-123">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a793a-123">The method completed successfully.</span></span>|  
|<span data-ttu-id="a793a-124">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a793a-124">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a793a-125">O buffer de diretório não é grande o suficiente para armazenar o caminho do diretório.</span><span class="sxs-lookup"><span data-stu-id="a793a-125">The directory buffer is not large enough to store the directory path.</span></span><br /><br /> <span data-ttu-id="a793a-126">- ou -</span><span class="sxs-lookup"><span data-stu-id="a793a-126">- or -</span></span><br /><br /> <span data-ttu-id="a793a-127">O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="a793a-127">The version buffer is not large enough to store the version string.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a793a-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="a793a-128">Remarks</span></span>  
 <span data-ttu-id="a793a-129">O método `GetRequestedRuntimeInfo` retorna informações de tempo de execução sobre a versão carregada no processo, que não é necessariamente a versão mais recente instalada no computador.</span><span class="sxs-lookup"><span data-stu-id="a793a-129">The `GetRequestedRuntimeInfo` method returns run-time information about the version loaded into the process, which is not necessarily the latest version installed on the computer.</span></span>  
  
 <span data-ttu-id="a793a-130">Na versão .NET Framework 2,0, você pode obter informações sobre a versão instalada mais recente usando o método `GetRequestedRuntimeInfo` da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="a793a-130">In the .NET Framework version 2.0, you can get information about the latest installed version by using the `GetRequestedRuntimeInfo` method as follows:</span></span>  
  
- <span data-ttu-id="a793a-131">Especifique os parâmetros `pExe`, `pwszVersion`e `pConfigurationFile` como NULL.</span><span class="sxs-lookup"><span data-stu-id="a793a-131">Specify the `pExe`, `pwszVersion`, and `pConfigurationFile` parameters as null.</span></span>  
  
- <span data-ttu-id="a793a-132">Especifique o sinalizador RUNTIME_INFO_UPGRADE_VERSION nas enumerações de `RUNTIME_INFO_FLAGS` para o parâmetro `runtimeInfoFlags`.</span><span class="sxs-lookup"><span data-stu-id="a793a-132">Specify the RUNTIME_INFO_UPGRADE_VERSION flag in the `RUNTIME_INFO_FLAGS` enumerations for the `runtimeInfoFlags` parameter.</span></span>  
  
 <span data-ttu-id="a793a-133">O método `GetRequestedRuntimeInfo` não retorna a versão mais recente do CLR nas seguintes circunstâncias:</span><span class="sxs-lookup"><span data-stu-id="a793a-133">The `GetRequestedRuntimeInfo` method does not return the latest CLR version in the following circumstances:</span></span>  
  
- <span data-ttu-id="a793a-134">Existe um arquivo de configuração de aplicativo que especifica o carregamento de uma versão CLR específica.</span><span class="sxs-lookup"><span data-stu-id="a793a-134">An application configuration file that specifies loading a particular CLR version exists.</span></span> <span data-ttu-id="a793a-135">Observe que o .NET Framework usará o arquivo de configuração mesmo se você especificar NULL para o parâmetro `pConfigurationFile`.</span><span class="sxs-lookup"><span data-stu-id="a793a-135">Note that the .NET Framework will use the configuration file even if you specify null for the `pConfigurationFile` parameter.</span></span>  
  
- <span data-ttu-id="a793a-136">O método [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) foi chamado especificando uma versão anterior do CLR.</span><span class="sxs-lookup"><span data-stu-id="a793a-136">The [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) method was called specifying an earlier CLR version.</span></span>  
  
- <span data-ttu-id="a793a-137">Um aplicativo que foi compilado para uma versão anterior do CLR está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="a793a-137">An application that was compiled for an earlier CLR version is currently running.</span></span>  
  
 <span data-ttu-id="a793a-138">Para o parâmetro `runtimeInfoFlags`, você pode especificar apenas uma das constantes de arquitetura da enumeração `RUNTIME_INFO_FLAGS` de cada vez:</span><span class="sxs-lookup"><span data-stu-id="a793a-138">For the `runtimeInfoFlags` parameter, you can specify only one of the architecture constants of the `RUNTIME_INFO_FLAGS` enumeration at a time:</span></span>  
  
- <span data-ttu-id="a793a-139">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="a793a-139">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="a793a-140">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="a793a-140">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="a793a-141">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="a793a-141">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a793a-142">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a793a-142">Requirements</span></span>  
 <span data-ttu-id="a793a-143">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a793a-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a793a-144">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a793a-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a793a-145">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a793a-145">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a793a-146">**Versões do .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a793a-146">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a793a-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a793a-147">See also</span></span>

- [<span data-ttu-id="a793a-148">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="a793a-148">GetRequestedRuntimeVersion Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)
- [<span data-ttu-id="a793a-149">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="a793a-149">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)
- [<span data-ttu-id="a793a-150">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="a793a-150">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
