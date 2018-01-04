---
title: "Função GetRequestedRuntimeVersion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRequestedRuntimeVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: GetRequestedRuntimeVersion
helpviewer_keywords: GetRequestedRuntimeVersion function [.NET Framework hosting]
ms.assetid: 82f596a4-483d-4509-b0c5-a84c53c3da1b
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13309a7362f468d3711176db2adc7a82e3b949d3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getrequestedruntimeversion-function"></a><span data-ttu-id="92674-102">Função GetRequestedRuntimeVersion</span><span class="sxs-lookup"><span data-stu-id="92674-102">GetRequestedRuntimeVersion Function</span></span>
<span data-ttu-id="92674-103">Obtém o número de versão do common language runtime (CLR) solicitado pelo aplicativo especificado.</span><span class="sxs-lookup"><span data-stu-id="92674-103">Gets the version number of the common language runtime (CLR) requested by the specified application.</span></span> <span data-ttu-id="92674-104">Se essa versão não estiver instalado, obtém a versão mais recente está instalada antes da versão solicitada.</span><span class="sxs-lookup"><span data-stu-id="92674-104">If that version is not installed, gets the most recent version that is installed before the requested version.</span></span>  
  
 <span data-ttu-id="92674-105">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="92674-105">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92674-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92674-106">Syntax</span></span>  
  
```  
HRESULT GetRequestedRuntimeVersion (  
    [in]  LPWSTR  pExe,   
    [out] LPWSTR  pVersion,   
    [in]  DWORD   cchBuffer,   
    [out] DWORD  *pdwLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92674-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92674-107">Parameters</span></span>  
 `pExe`  
 <span data-ttu-id="92674-108">[in] O nome do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92674-108">[in] The name of the application.</span></span>  
  
 `pVersion`  
 <span data-ttu-id="92674-109">[out] Um buffer que contém a cadeia de caracteres de número de versão após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="92674-109">[out] A buffer that contains the version number string upon successful completion.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="92674-110">[in] O comprimento do buffer de versão.</span><span class="sxs-lookup"><span data-stu-id="92674-110">[in] The length of the version buffer.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="92674-111">[out] Um ponteiro para o comprimento da cadeia de número de versão.</span><span class="sxs-lookup"><span data-stu-id="92674-111">[out] A pointer to the length of the version number string.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92674-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="92674-112">Return Value</span></span>  
 <span data-ttu-id="92674-113">Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="92674-113">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="92674-114">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="92674-114">Return code</span></span>|<span data-ttu-id="92674-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="92674-115">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="92674-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="92674-116">S_OK</span></span>|<span data-ttu-id="92674-117">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="92674-117">The method completed successfully.</span></span>|  
|<span data-ttu-id="92674-118">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="92674-118">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="92674-119">O buffer de versão não é grande o suficiente para armazenar a cadeia de caracteres de versão.</span><span class="sxs-lookup"><span data-stu-id="92674-119">The version buffer is not large enough to store the version string.</span></span>|  
|<span data-ttu-id="92674-120">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="92674-120">E_POINTER</span></span>|<span data-ttu-id="92674-121">`pdwLength` é nulo.</span><span class="sxs-lookup"><span data-stu-id="92674-121">`pdwLength` is null.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92674-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92674-122">Requirements</span></span>  
 <span data-ttu-id="92674-123">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92674-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92674-124">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="92674-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92674-125">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="92674-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92674-126">**Versões do .NET framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92674-126">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92674-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92674-127">See Also</span></span>  
 [<span data-ttu-id="92674-128">Função GetRequestedRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="92674-128">GetRequestedRuntimeInfo Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)  
 [<span data-ttu-id="92674-129">Função GetVersionFromProcess</span><span class="sxs-lookup"><span data-stu-id="92674-129">GetVersionFromProcess Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)  
 [<span data-ttu-id="92674-130">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="92674-130">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
