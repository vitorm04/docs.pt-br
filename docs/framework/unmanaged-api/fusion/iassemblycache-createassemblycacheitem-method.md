---
title: Método IAssemblyCache::CreateAssemblyCacheItem
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c45257a76127adf2bcf9ab356639d4754d151bf6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430678"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="1231f-102">Método IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="1231f-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="1231f-103">Obtém uma referência a um novo [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="1231f-103">Gets a reference to a new [IAssemblyCacheItem](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1231f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1231f-104">Syntax</span></span>  
  
```  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1231f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1231f-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="1231f-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="1231f-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="1231f-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="1231f-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="1231f-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0X00000001)</span><span class="sxs-lookup"><span data-stu-id="1231f-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
-   <span data-ttu-id="1231f-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0X00000002)</span><span class="sxs-lookup"><span data-stu-id="1231f-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="1231f-110">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="1231f-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="1231f-111">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="1231f-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="1231f-112">[out] Retornado `IAssemblyCacheItem` ponteiro.</span><span class="sxs-lookup"><span data-stu-id="1231f-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="1231f-113">[in, opcional] Uncanonicalized, separados por vírgulas `name=value` pares.</span><span class="sxs-lookup"><span data-stu-id="1231f-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1231f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1231f-114">Requirements</span></span>  
 <span data-ttu-id="1231f-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1231f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1231f-116">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="1231f-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="1231f-117">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1231f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1231f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1231f-118">See Also</span></span>  
 [<span data-ttu-id="1231f-119">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="1231f-119">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)  
 [<span data-ttu-id="1231f-120">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="1231f-120">IAssemblyCacheItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycacheitem-interface.md)
