---
title: Função CorLaunchApplication
ms.date: 03/30/2017
api_name:
- CorLaunchApplication
api_location:
- mscoree.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CorLaunchApplication
helpviewer_keywords:
- CorLaunchApplication function [.NET Framework hosting]
ms.assetid: 71f362a9-8fe2-47ce-9302-05a645cf3d7d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c997ab107ba3ceb7773bc9235b9c9dcd4d97df8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231442"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="b8ed3-102">Função CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="b8ed3-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="b8ed3-103">Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="b8ed3-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8ed3-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8ed3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8ed3-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b8ed3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8ed3-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="b8ed3-107">[in] Um valor igual a [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeração que especifica o tipo de host que está iniciando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="b8ed3-108">[in] O nome completo do aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="b8ed3-109">[in] O número de caminhos do manifesto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="b8ed3-110">[in] Uma matriz de cadeias de caracteres, cada um deles especifica um caminho para um manifesto do aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="b8ed3-111">[in] O número de itens de dados de ativação para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="b8ed3-112">[in] Uma matriz de cadeias de caracteres, cada um deles é um item de dados de ativação para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="b8ed3-113">[out] Um ponteiro para obter informações sobre o processo no qual o aplicativo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="b8ed3-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8ed3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8ed3-114">Requirements</span></span>  
 <span data-ttu-id="b8ed3-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8ed3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8ed3-116">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b8ed3-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b8ed3-117">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b8ed3-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b8ed3-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8ed3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8ed3-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8ed3-119">See also</span></span>

- [<span data-ttu-id="b8ed3-120">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="b8ed3-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
