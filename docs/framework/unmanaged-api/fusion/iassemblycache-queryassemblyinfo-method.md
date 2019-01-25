---
title: Método IAssemblyCache::QueryAssemblyInfo
ms.date: 03/30/2017
api_name:
- IAssemblyCache.QueryAssemblyInfo
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::QueryAssemblyInfo
helpviewer_keywords:
- IAssemblyCache::QueryAssemblyInfo method [.NET Framework fusion]
- QueryAssemblyInfo method [.NET Framework fusion]
ms.assetid: 09313cb5-06f6-43bd-94f4-1055c6b0c99a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1c3d20b1b9470c744f6dca9ef638555b9322c1c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658111"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="89abb-102">Método IAssemblyCache::QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="89abb-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="89abb-103">Obtém os dados solicitados sobre o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="89abb-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89abb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="89abb-104">Syntax</span></span>  
  
```  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="89abb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="89abb-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="89abb-106">[in] Sinalizadores definidos no Fusion.idl.</span><span class="sxs-lookup"><span data-stu-id="89abb-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="89abb-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="89abb-107">The following values are supported:</span></span>  
  
-   <span data-ttu-id="89abb-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="89abb-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
-   <span data-ttu-id="89abb-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="89abb-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="89abb-110">[in] O nome do assembly para o qual os dados serão recuperados.</span><span class="sxs-lookup"><span data-stu-id="89abb-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="89abb-111">[no, out] Uma [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) estrutura que contém dados sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="89abb-111">[in, out] An [ASSEMBLY_INFO](../../../../docs/framework/unmanaged-api/fusion/assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89abb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="89abb-112">Requirements</span></span>  
 <span data-ttu-id="89abb-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89abb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89abb-114">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="89abb-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="89abb-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89abb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89abb-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="89abb-116">See also</span></span>
- [<span data-ttu-id="89abb-117">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="89abb-117">IAssemblyCache Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)
