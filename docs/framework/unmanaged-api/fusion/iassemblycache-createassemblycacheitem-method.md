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
ms.openlocfilehash: e3e50538bde8fe3509b49e3dbcb031875e6863e5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127115"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="68c43-102">Método IAssemblyCache::CreateAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="68c43-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>
<span data-ttu-id="68c43-103">Obtém uma referência a um novo objeto [IAssemblyCacheItem](iassemblycacheitem-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="68c43-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68c43-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68c43-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68c43-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="68c43-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="68c43-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="68c43-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="68c43-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="68c43-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="68c43-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="68c43-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="68c43-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="68c43-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="68c43-110">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="68c43-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="68c43-111">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="68c43-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="68c43-112">fora O ponteiro de `IAssemblyCacheItem` retornado.</span><span class="sxs-lookup"><span data-stu-id="68c43-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="68c43-113">[in, opcional] Pares de `name=value` não canônicos separados por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="68c43-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68c43-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68c43-114">Requirements</span></span>  
 <span data-ttu-id="68c43-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68c43-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68c43-116">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="68c43-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="68c43-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68c43-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c43-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68c43-118">See also</span></span>

- [<span data-ttu-id="68c43-119">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="68c43-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="68c43-120">Interface IAssemblyCacheItem</span><span class="sxs-lookup"><span data-stu-id="68c43-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
