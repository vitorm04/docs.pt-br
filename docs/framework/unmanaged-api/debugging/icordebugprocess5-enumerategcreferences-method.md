---
title: Método ICorDebugProcess5::EnumerateGCReferences
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateGCReferences
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateGCReferences
helpviewer_keywords:
- EnumerateGCReferences method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateGCReferences method [.NET Framework debugging]
ms.assetid: 86c397c3-81d8-463e-a248-3cbe06c44d9d
topic_type:
- apiref
ms.openlocfilehash: 84b5da043f9bd437ee9099135ba865c1ab23bb9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129665"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="e0841-102">Método ICorDebugProcess5::EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="e0841-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="e0841-103">Obtém um enumerador para todos os objetos que devem ser coletados pelo lixo em um processo.</span><span class="sxs-lookup"><span data-stu-id="e0841-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0841-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e0841-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0841-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e0841-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="e0841-106">no Um valor booliano que indica se referências fracas também devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="e0841-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="e0841-107">Se `enumerateWeakReferences` for `true`, o enumerador `ppEnum` incluirá referências fortes e referências fracas.</span><span class="sxs-lookup"><span data-stu-id="e0841-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="e0841-108">Se `enumerateWeakReferences` for `false`, o enumerador incluirá apenas referências fortes.</span><span class="sxs-lookup"><span data-stu-id="e0841-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="e0841-109">fora Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a serem coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="e0841-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0841-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="e0841-110">Remarks</span></span>  
 <span data-ttu-id="e0841-111">Esse método fornece uma maneira de determinar a cadeia de raiz completa para qualquer objeto gerenciado em um processo e pode ser usado para determinar por que um objeto ainda está ativo.</span><span class="sxs-lookup"><span data-stu-id="e0841-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0841-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e0841-112">Requirements</span></span>  
 <span data-ttu-id="e0841-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0841-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0841-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0841-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0841-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0841-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0841-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0841-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0841-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0841-117">See also</span></span>

- [<span data-ttu-id="e0841-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="e0841-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="e0841-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e0841-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
