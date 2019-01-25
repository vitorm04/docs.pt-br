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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8614dd612fff2886c4e44a977d05a575fce74eec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648937"
---
# <a name="icordebugcodegetiltonativemapping-method"></a><span data-ttu-id="c31db-102">Método ICorDebugCode::GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="c31db-102">ICorDebugCode::GetILToNativeMapping Method</span></span>
<span data-ttu-id="c31db-103">Obtém uma matriz de instâncias de "COR_DEBUG_IL_TO_NATIVE_MAP" que representam os mapeamentos da Microsoft intermediate language (MSIL) deslocamentos para deslocamentos nativos.</span><span class="sxs-lookup"><span data-stu-id="c31db-103">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from Microsoft intermediate language (MSIL) offsets to native offsets.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c31db-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c31db-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c31db-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c31db-105">Parameters</span></span>  
 `cMap`  
 <span data-ttu-id="c31db-106">[in] O tamanho do `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="c31db-106">[in] The size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="c31db-107">[out] Um ponteiro para o número real de elementos retornados no `map` matriz.</span><span class="sxs-lookup"><span data-stu-id="c31db-107">[out] A pointer to the actual number of elements returned in the `map` array.</span></span>  
  
 `map`  
 <span data-ttu-id="c31db-108">[out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada um deles representa um mapeamento de um deslocamento MSIL para um deslocamento nativo.</span><span class="sxs-lookup"><span data-stu-id="c31db-108">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` stuctures, each of which represents a mapping from an MSIL offset to a native offset.</span></span>  
  
 <span data-ttu-id="c31db-109">Não há nenhuma ordem para a matriz de elementos retornados.</span><span class="sxs-lookup"><span data-stu-id="c31db-109">There is no ordering to the array of elements returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c31db-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c31db-110">Remarks</span></span>  
 <span data-ttu-id="c31db-111">O `GetILToNativeMapping` método retorna resultados significativos apenas se essa instância de "ICorDebugCode" representa o código nativo foi just-in-time (JIT) compilado a partir de código MSIL.</span><span class="sxs-lookup"><span data-stu-id="c31db-111">The `GetILToNativeMapping` method returns meaningful results only if this "ICorDebugCode" instance represents native code that was just-in-time (JIT) compiled from MSIL code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c31db-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c31db-112">Requirements</span></span>  
 <span data-ttu-id="c31db-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c31db-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c31db-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c31db-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c31db-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c31db-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c31db-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c31db-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c31db-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c31db-117">See also</span></span>
- [<span data-ttu-id="c31db-118">Interface1 ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="c31db-118">ICorDebugCode Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
