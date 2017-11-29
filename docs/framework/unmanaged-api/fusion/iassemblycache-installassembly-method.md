---
title: "Método IAssemblyCache::InstallAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.InstallAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d1207c2dc5b29b8de084ccb9145e886f34e8144b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="8fefc-102">Método IAssemblyCache::InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="8fefc-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="8fefc-103">Instala o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="8fefc-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fefc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8fefc-104">Syntax</span></span>  
  
```  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8fefc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8fefc-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="8fefc-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="8fefc-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="8fefc-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="8fefc-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="8fefc-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="8fefc-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="8fefc-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="8fefc-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="8fefc-110">[in] O caminho para o manifesto do assembly a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="8fefc-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="8fefc-111">[in] Um [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) estrutura que contém dados para a instalação.</span><span class="sxs-lookup"><span data-stu-id="8fefc-111">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fefc-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8fefc-112">Requirements</span></span>  
 <span data-ttu-id="8fefc-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fefc-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fefc-114">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="8fefc-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="8fefc-115">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fefc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fefc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8fefc-116">See Also</span></span>  
 [<span data-ttu-id="8fefc-117">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="8fefc-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
