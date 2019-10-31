---
title: Método IAssemblyCache::InstallAssembly
ms.date: 03/30/2017
api_name:
- IAssemblyCache.InstallAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::InstallAssembly
helpviewer_keywords:
- InstallAssembly method [.NET Framework fusion]
- IAssemblyCache::InstallAssembly method [.NET Framework fusion]
ms.assetid: 33c1d269-c85e-4cb1-b0e6-1c510c8fb5fa
topic_type:
- apiref
ms.openlocfilehash: ec08c786992996ec6f44038ff3c1596cada88484
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127079"
---
# <a name="iassemblycacheinstallassembly-method"></a><span data-ttu-id="35a2d-102">Método IAssemblyCache::InstallAssembly</span><span class="sxs-lookup"><span data-stu-id="35a2d-102">IAssemblyCache::InstallAssembly Method</span></span>
<span data-ttu-id="35a2d-103">Instala o assembly especificado no cache de assembly global.</span><span class="sxs-lookup"><span data-stu-id="35a2d-103">Installs the specified assembly in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35a2d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35a2d-104">Syntax</span></span>  
  
```cpp  
HRESULT InstallAssembly (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszManifestFilePath,  
    [in] LPCFUSION_INSTALL_REFERENCE pRefData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35a2d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35a2d-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="35a2d-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="35a2d-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="35a2d-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="35a2d-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="35a2d-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="35a2d-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="35a2d-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="35a2d-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pszManifestFilePath`  
 <span data-ttu-id="35a2d-110">no O caminho para o manifesto para o assembly a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="35a2d-110">[in] The path to the manifest for the assembly to install.</span></span>  
  
 `pRefData`  
 <span data-ttu-id="35a2d-111">no Uma estrutura [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) que contém dados para a instalação.</span><span class="sxs-lookup"><span data-stu-id="35a2d-111">[in] A [FUSION_INSTALL_REFERENCE](fusion-install-reference-structure.md) structure that contains data for the installation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35a2d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35a2d-112">Requirements</span></span>  
 <span data-ttu-id="35a2d-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35a2d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35a2d-114">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="35a2d-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="35a2d-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35a2d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35a2d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35a2d-116">See also</span></span>

- [<span data-ttu-id="35a2d-117">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="35a2d-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
