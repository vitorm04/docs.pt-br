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
ms.openlocfilehash: e975db68252e866a0bf7898f1c9d3cbe67bbe24f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134574"
---
# <a name="iassemblycachequeryassemblyinfo-method"></a><span data-ttu-id="a6597-102">Método IAssemblyCache::QueryAssemblyInfo</span><span class="sxs-lookup"><span data-stu-id="a6597-102">IAssemblyCache::QueryAssemblyInfo Method</span></span>
<span data-ttu-id="a6597-103">Obtém os dados solicitados sobre o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="a6597-103">Gets the requested data about the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6597-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6597-104">Syntax</span></span>  
  
```cpp  
HRESULT QueryAssemblyInfo (  
    [in] DWORD dwFlags,  
    [in] LPCWSTR pszAssemblyName,  
    [in, out] ASSEMBLY_INFO *pAsmInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6597-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a6597-105">Parameters</span></span>  
 `dwFlags`  
 <span data-ttu-id="a6597-106">no Sinalizadores definidos em Fusion. idl.</span><span class="sxs-lookup"><span data-stu-id="a6597-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="a6597-107">Há suporte para os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="a6597-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="a6597-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="a6597-108">QUERYASMINFO_FLAG_VALIDATE (0x00000001)</span></span>  
  
- <span data-ttu-id="a6597-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="a6597-109">QUERYASMINFO_FLAG_GETSIZE (0x00000002)</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="a6597-110">no O nome do assembly para o qual os dados serão recuperados.</span><span class="sxs-lookup"><span data-stu-id="a6597-110">[in] The name of the assembly for which data will be retrieved.</span></span>  
  
 `pAsmInfo`  
 <span data-ttu-id="a6597-111">[entrada, saída] Uma estrutura [ASSEMBLY_INFO](assembly-info-structure.md) que contém dados sobre o assembly.</span><span class="sxs-lookup"><span data-stu-id="a6597-111">[in, out] An [ASSEMBLY_INFO](assembly-info-structure.md) structure that contains data about the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6597-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6597-112">Requirements</span></span>  
 <span data-ttu-id="a6597-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6597-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6597-114">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a6597-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a6597-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6597-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6597-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6597-116">See also</span></span>

- [<span data-ttu-id="a6597-117">Interface IAssemblyCache</span><span class="sxs-lookup"><span data-stu-id="a6597-117">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
