---
title: "Função CorLaunchApplication"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type: COM
f1_keywords: CorLaunchApplication
helpviewer_keywords: CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d6246ab600438e2237dcbe531d9d7641c0897d81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="63729-102">Função CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="63729-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="63729-103">Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63729-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="63729-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63729-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63729-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63729-105">Syntax</span></span>  
  
```  
HRESULT CorLaunchApplication (  
    [in]  HOST_TYPE                dwClickOnceHost,  
    [in]  LPCWSTR                  pwzAppFullName,  
    [in]  DWORD                    dwManifestPaths,  
    [in]  LPCWSTR                 *ppwzManifestPaths,  
    [in]  DWORD                    dwActivationData,  
    [in]  LPCWSTR                 *ppwzActivationData,  
    [out] LPPROCESS_INFORMATION    lpProcessInformation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="63729-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63729-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="63729-107">[in] Um valor de [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeração que especifica o tipo de host que está iniciando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63729-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="63729-108">[in] O nome completo do aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="63729-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="63729-109">[in] O número de caminhos do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63729-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="63729-110">[in] Uma matriz de cadeias de caracteres, cada uma delas Especifica um caminho para um manifesto do aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="63729-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="63729-111">[in] O número de itens de dados de ativação para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="63729-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="63729-112">[in] Uma matriz de cadeias de caracteres, cada um deles é um item de dados de ativação para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="63729-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="63729-113">[out] Um ponteiro para obter informações sobre o processo no qual o aplicativo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="63729-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63729-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63729-114">Requirements</span></span>  
 <span data-ttu-id="63729-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63729-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63729-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="63729-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63729-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63729-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63729-118">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63729-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63729-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63729-119">See Also</span></span>  
 [<span data-ttu-id="63729-120">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="63729-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
