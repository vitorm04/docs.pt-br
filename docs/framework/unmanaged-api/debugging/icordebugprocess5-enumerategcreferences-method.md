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
ms.openlocfilehash: a97c14d83f99c847bb8569a33e175ab6eb5bccd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178615"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="ca18d-102">Método ICorDebugProcess5::EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="ca18d-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="ca18d-103">Recebe um enumerador para todos os objetos que devem ser coletados em um processo.</span><span class="sxs-lookup"><span data-stu-id="ca18d-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca18d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ca18d-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca18d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="ca18d-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="ca18d-106">[em] Um valor booleano que indica se referências fracas também devem ser enumeradas.</span><span class="sxs-lookup"><span data-stu-id="ca18d-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="ca18d-107">Se `enumerateWeakReferences` `true`for, `ppEnum` o enumerador inclui referências fortes e referências fracas.</span><span class="sxs-lookup"><span data-stu-id="ca18d-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="ca18d-108">Se `enumerateWeakReferences` `false`for, o enumerador inclui apenas referências fortes.</span><span class="sxs-lookup"><span data-stu-id="ca18d-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="ca18d-109">[fora] Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) que é um enumerador para que os objetos sejam coletados em lixo.</span><span class="sxs-lookup"><span data-stu-id="ca18d-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca18d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="ca18d-110">Remarks</span></span>  
 <span data-ttu-id="ca18d-111">Este método fornece uma maneira de determinar a cadeia de raiz completa para qualquer objeto gerenciado em um processo e pode ser usado para determinar por que um objeto ainda está vivo.</span><span class="sxs-lookup"><span data-stu-id="ca18d-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca18d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ca18d-112">Requirements</span></span>  
 <span data-ttu-id="ca18d-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca18d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca18d-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca18d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca18d-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca18d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca18d-116">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca18d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca18d-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="ca18d-117">See also</span></span>

- [<span data-ttu-id="ca18d-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="ca18d-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="ca18d-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="ca18d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
