---
title: Método IAssemblyCache::UninstallAssembly
ms.date: 03/30/2017
api_name:
- IAssemblyCache.UninstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::UninstallAssembly
helpviewer_keywords:
- UninstallAssembly method [.NET Framework fusion]
- IAssemblyCache::UninstallAssembly method [.NET Framework fusion]
ms.assetid: 973b2c44-8dfc-40c1-9035-10f4846627e9
topic_type:
- apiref
ms.openlocfilehash: 539a8edf6d7248235a6e672edc9464679a2eab82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134507"
---
# <a name="iassemblycacheuninstallassembly-method"></a><span data-ttu-id="d8b95-102">Método IAssemblyCache::UninstallAssembly</span><span class="sxs-lookup"><span data-stu-id="d8b95-102">IAssemblyCache::UninstallAssembly Method</span></span>
<span data-ttu-id="d8b95-103">Desinstala o assembly especificado do cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="d8b95-103">Uninstalls the specified assembly from the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b95-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d8b95-104">Syntax</span></span>  
  
```cpp  
HRESULT UninstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData,  
    [out, optional] ULONG *pulDisposition  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8b95-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d8b95-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="d8b95-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="d8b95-106">[in] Flags defined in Fusion.idl.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="d8b95-107">no O nome do assembly a ser desinstalado.</span><span class="sxs-lookup"><span data-stu-id="d8b95-107">[in] The name of the assembly to uninstall.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="d8b95-108">no Uma estrutura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) que contém os dados de instalação para o assembly.</span><span class="sxs-lookup"><span data-stu-id="d8b95-108">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains the installation data for the assembly.</span></span>  
  
 `pulDisposition`  
 <span data-ttu-id="d8b95-109">[saída, opcional] Um dos valores de disposição definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="d8b95-109">[out, optional] One of the disposition values defined in Fusion.idl.</span></span> <span data-ttu-id="d8b95-110">Os valores possíveis incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d8b95-110">Possible values include the following:</span></span>  
  
- <span data-ttu-id="d8b95-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span><span class="sxs-lookup"><span data-stu-id="d8b95-111">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_UNINSTALLED (1)</span></span>  
  
- <span data-ttu-id="d8b95-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span><span class="sxs-lookup"><span data-stu-id="d8b95-112">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_STILL_IN_USE (2)</span></span>  
  
- <span data-ttu-id="d8b95-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span><span class="sxs-lookup"><span data-stu-id="d8b95-113">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_ALREADY_UNINSTALLED (3)</span></span>  
  
- <span data-ttu-id="d8b95-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span><span class="sxs-lookup"><span data-stu-id="d8b95-114">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_DELETE_PENDING (4)</span></span>  
  
- <span data-ttu-id="d8b95-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span><span class="sxs-lookup"><span data-stu-id="d8b95-115">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_HAS_INSTALL_REFERENCES (5)</span></span>  
  
- <span data-ttu-id="d8b95-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span><span class="sxs-lookup"><span data-stu-id="d8b95-116">IASSEMBLYCACHE_UNINSTALL_DISPOSITION_REFERENCE_NOT_FOUND (6)</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8b95-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d8b95-117">Requirements</span></span>  
 <span data-ttu-id="d8b95-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8b95-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b95-119">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d8b95-119">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d8b95-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b95-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b95-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8b95-121">See also</span></span>

- [<span data-ttu-id="d8b95-122">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="d8b95-122">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
