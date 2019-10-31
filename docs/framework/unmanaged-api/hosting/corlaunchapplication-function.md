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
ms.openlocfilehash: e01698d2d8491b2496bb664c13dca97964cd1481
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136939"
---
# <a name="corlaunchapplication-function"></a><span data-ttu-id="d82f0-102">Função CorLaunchApplication</span><span class="sxs-lookup"><span data-stu-id="d82f0-102">CorLaunchApplication Function</span></span>
<span data-ttu-id="d82f0-103">Inicia o aplicativo no caminho de rede especificado, usando os manifestos especificados e outros dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d82f0-103">Starts the application at the specified network path, using the specified manifests and other application data.</span></span>  
  
 <span data-ttu-id="d82f0-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="d82f0-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82f0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d82f0-105">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="d82f0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d82f0-106">Parameters</span></span>  
 `dwClickOnceHost`  
 <span data-ttu-id="d82f0-107">no Um valor da enumeração [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) que especifica o tipo de host que está iniciando o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d82f0-107">[in] A value of the [HOST_TYPE](../../../../docs/framework/unmanaged-api/hosting/host-type-enumeration.md) enumeration that specifies the type of host that is launching the application.</span></span>  
  
 `pwzAppFullName`  
 <span data-ttu-id="d82f0-108">no O nome completo do aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="d82f0-108">[in] The full name of the application that is being launched.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="d82f0-109">no O número de caminhos de manifesto para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d82f0-109">[in] The number of manifest paths for the application.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="d82f0-110">no Uma matriz de cadeias de caracteres, cada uma delas especifica um caminho para um manifesto para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="d82f0-110">[in] An array of strings, each of which specifies a path to a manifest for the application that is being launched.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="d82f0-111">no O número de itens de dados de ativação para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="d82f0-111">[in] The number of activation data items for the application that is being launched.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="d82f0-112">no Uma matriz de cadeias de caracteres, cada uma delas é um item de dados de ativação para o aplicativo que está sendo iniciado.</span><span class="sxs-lookup"><span data-stu-id="d82f0-112">[in] An array of strings, each of which is an activation data item for the application that is being launched.</span></span>  
  
 `lpProcessInformation`  
 <span data-ttu-id="d82f0-113">fora Um ponteiro para informações sobre o processo no qual o aplicativo foi carregado.</span><span class="sxs-lookup"><span data-stu-id="d82f0-113">[out] A pointer to information about the process in which the application has been loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82f0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d82f0-114">Requirements</span></span>  
 <span data-ttu-id="d82f0-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82f0-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82f0-116">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d82f0-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d82f0-117">**Biblioteca:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d82f0-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d82f0-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82f0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d82f0-119">See also</span></span>

- [<span data-ttu-id="d82f0-120">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="d82f0-120">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
