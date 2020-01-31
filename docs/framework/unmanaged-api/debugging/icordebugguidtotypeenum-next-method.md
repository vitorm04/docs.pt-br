---
title: Método ICorDebugGuidToTypeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: 76cab0b8b5f16f24c62e31be2707c95c7e557034
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777641"
---
# <a name="icordebugguidtotypeenumnext-method"></a><span data-ttu-id="df531-102">Método ICorDebugGuidToTypeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="df531-102">ICorDebugGuidToTypeEnum::Next Method</span></span>
<span data-ttu-id="df531-103">Obtém o número especificado de instâncias de [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) que MAPEIAm GUIDs para informações de tipo.</span><span class="sxs-lookup"><span data-stu-id="df531-103">Gets the specified number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) instances that map GUIDs to type information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df531-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df531-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df531-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df531-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="df531-106">no O número de objetos de mapeamento GUID-to-Type a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="df531-106">[in] The number of GUID-to-type mapping objects to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="df531-107">fora Uma matriz de ponteiros, cada um dos quais aponta para um objeto [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) que MAPEIA um GUID de Windows Runtime para seu objeto ICorDebugType correspondente.</span><span class="sxs-lookup"><span data-stu-id="df531-107">[out] An array of pointers, each of which points to a [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) object that maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="df531-108">fora Um ponteiro para o número de objetos [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) realmente retornados em `values`.</span><span class="sxs-lookup"><span data-stu-id="df531-108">[out] A pointer to the number of [CorDebugGuidToTypeMapping](cordebugguidtotypemapping-structure.md) objects actually returned in `values`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df531-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="df531-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df531-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="df531-110">Requirements</span></span>  
 <span data-ttu-id="df531-111">**Plataformas:** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="df531-111">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="df531-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df531-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df531-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df531-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df531-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df531-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df531-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="df531-115">See also</span></span>

- [<span data-ttu-id="df531-116">Interface ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="df531-116">ICorDebugGuidToTypeEnum Interface</span></span>](icordebugguidtotypeenum-interface.md)
- [<span data-ttu-id="df531-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="df531-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
