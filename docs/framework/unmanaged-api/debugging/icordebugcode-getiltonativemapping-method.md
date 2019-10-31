---
title: Método ICorDebugCode::GetILToNativeMapping
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
ms.openlocfilehash: 011da6aacbf4c40420329952f47b1fabdfc2c1a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125626"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="7faa4-102">Método ICorDebugCode::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="7faa4-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="7faa4-103">Obtém uma matriz de instâncias "COR_DEBUG_IL_TO_NATIVE_MAP" que representam mapeamentos de deslocamentos de MSIL (Microsoft Intermediate Language) para deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="7faa4-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7faa4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7faa4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7faa4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7faa4-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="7faa4-106">no O tamanho da matriz de `map`.</span><span class="sxs-lookup"><span data-stu-id="7faa4-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="7faa4-107">fora Um ponteiro para o número real de elementos retornados na matriz de `map`.</span><span class="sxs-lookup"><span data-stu-id="7faa4-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="7faa4-108">fora Uma matriz de estruturas `COR_DEBUG_IL_TO_NATIVE_MAP`, cada uma representando um mapeamento de um deslocamento MSIL para um deslocamento nativo.</span><span class="sxs-lookup"><span data-stu-id="7faa4-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="7faa4-109">Não há nenhuma ordem para a matriz de elementos retornada.</span><span class="sxs-lookup"><span data-stu-id="7faa4-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7faa4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7faa4-110">Remarks</span></span>  
 <span data-ttu-id="7faa4-111">O método `GetILToNativeMapping` retorna resultados significativos somente se essa instância "ICorDebugCode" representa o código nativo que era JIT (just-in-time) compilado do código MSIL.</span><span class="sxs-lookup"><span data-stu-id="7faa4-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7faa4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7faa4-112">Requirements</span></span>  
 <span data-ttu-id="7faa4-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7faa4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7faa4-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7faa4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7faa4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7faa4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7faa4-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7faa4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7faa4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7faa4-117">See also</span></span>

- [<span data-ttu-id="7faa4-118">Interface ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="7faa4-118">ICorDebugCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
