---
title: Método IAssemblyName::IsEqual
ms.date: 03/30/2017
api_name:
- IAssemblyName.IsEqual
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type:
- apiref
ms.openlocfilehash: 23bc251053dd27a7c5accb48ab4759ecdb79fe09
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134302"
---
# <a name="iassemblynameisequal-method"></a><span data-ttu-id="f0291-102">Método IAssemblyName::IsEqual</span><span class="sxs-lookup"><span data-stu-id="f0291-102">IAssemblyName::IsEqual Method</span></span>
<span data-ttu-id="f0291-103">Determina se um objeto [IAssemblyName](iassemblyname-interface.md) especificado é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificados.</span><span class="sxs-lookup"><span data-stu-id="f0291-103">Determines whether a specified [IAssemblyName](iassemblyname-interface.md) object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0291-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f0291-104">Syntax</span></span>  
  
```cpp  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0291-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f0291-105">Parameters</span></span>  
 `pName`  
 <span data-ttu-id="f0291-106">no O objeto `IAssemblyName` para o qual comparar esse `IAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="f0291-106">[in] The `IAssemblyName` object to which to compare this `IAssemblyName`.</span></span>  
  
 `dwCmpFlags`  
 <span data-ttu-id="f0291-107">no Uma combinação de bits de valores [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) que influencia a comparação.</span><span class="sxs-lookup"><span data-stu-id="f0291-107">[in] A bitwise combination of [ASM_CMP_FLAGS](asm-cmp-flags-enumeration.md) values that influence the comparison.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0291-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f0291-108">Requirements</span></span>  
 <span data-ttu-id="f0291-109">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0291-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0291-110">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f0291-110">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f0291-111">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0291-111">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0291-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f0291-112">See also</span></span>

- [<span data-ttu-id="f0291-113">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="f0291-113">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="f0291-114">Enumerações de fusão</span><span class="sxs-lookup"><span data-stu-id="f0291-114">Fusion Enumerations</span></span>](fusion-enumerations.md)
