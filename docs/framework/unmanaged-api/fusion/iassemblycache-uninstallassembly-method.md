---
title: "Método IAssemblyCache::UninstallAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyCache.UninstallAssembly
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d34b2793de58721c7d4863855106d4b231bccc54
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="b165e-102">Método IAssemblyCache::UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="b165e-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="b165e-103">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="b165e-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b165e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b165e-104">Syntax</span></span>  
  
```  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b165e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b165e-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="b165e-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b165e-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="b165e-107">[in] O nome do assembly para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="b165e-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="b165e-108">[in] Um [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) estrutura que contém os dados de instalação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="b165e-108">[in] A [FUSION_INSTALL_REFERENCE](../../../../docs/framework/unmanaged-api/fusion/fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="b165e-109">[out, opcional] Um dos valores de disposição definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="b165e-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="b165e-110">Os valores possíveis incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="b165e-110">Possible values include the following:</span></span>  
  
-   <span data-ttu-id="b165e-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="b165e-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
-   <span data-ttu-id="b165e-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="b165e-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
-   <span data-ttu-id="b165e-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="b165e-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
-   <span data-ttu-id="b165e-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="b165e-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
-   <span data-ttu-id="b165e-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="b165e-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
-   <span data-ttu-id="b165e-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="b165e-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b165e-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b165e-117">Requirements</span></span>  
 <span data-ttu-id="b165e-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b165e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b165e-119">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="b165e-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b165e-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b165e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b165e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b165e-121">See Also</span></span>  
 [<span data-ttu-id="b165e-122">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="b165e-122">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
