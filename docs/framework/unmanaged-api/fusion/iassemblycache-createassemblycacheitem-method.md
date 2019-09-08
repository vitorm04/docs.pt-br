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
ms.openlocfilehash: 215eb3a508a746230d36fdda3e8ba992287be62c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796821"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="5f5db-102">Método IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="5f5db-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="5f5db-103">Obtém uma referência a um novo objeto [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="5f5db-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f5db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f5db-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f5db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5f5db-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="5f5db-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="5f5db-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="5f5db-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="5f5db-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="5f5db-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="5f5db-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="5f5db-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="5f5db-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5f5db-110">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="5f5db-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5f5db-111">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="5f5db-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="5f5db-112">fora O ponteiro `IAssemblyCacheItem` retornado.</span><span class="sxs-lookup"><span data-stu-id="5f5db-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="5f5db-113">[in, opcional] Pares não canônicos e separados por `name=value` vírgulas.</span><span class="sxs-lookup"><span data-stu-id="5f5db-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f5db-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5f5db-114">Requirements</span></span>  
 <span data-ttu-id="5f5db-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f5db-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f5db-116">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5f5db-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5f5db-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f5db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f5db-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f5db-118">See also</span></span>

- [<span data-ttu-id="5f5db-119">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="5f5db-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="5f5db-120">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="5f5db-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
