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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b5f66099eb4b1cb84d9911567cac4255bf20480
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421390"
---
# <a name="icordebugprocess5enumerategcreferences-method"></a><span data-ttu-id="4b2d6-102">Método ICorDebugProcess5::EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="4b2d6-102">ICorDebugProcess5::EnumerateGCReferences Method</span></span>
<span data-ttu-id="4b2d6-103">Obtém um enumerador para todos os objetos que devem ser coletados como lixo em um processo.</span><span class="sxs-lookup"><span data-stu-id="4b2d6-103">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b2d6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4b2d6-104">Syntax</span></span>  
  
```  
HRESULT EnumerateGCReferences(  
    [in] Bool enumerateWeakReferences,   
    [out] ICorDebugGCReferenceEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4b2d6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4b2d6-105">Parameters</span></span>  
 `enumerateWeakReferences`  
 <span data-ttu-id="4b2d6-106">[in] Um valor booliano que indica se referências fracas devem também ser enumerados.</span><span class="sxs-lookup"><span data-stu-id="4b2d6-106">[in] A Boolean value that indicates whether weak references are also to be enumerated.</span></span> <span data-ttu-id="4b2d6-107">Se `enumerateWeakReferences` é `true`, o `ppEnum` enumerador inclui referências fortes e referências fracas.</span><span class="sxs-lookup"><span data-stu-id="4b2d6-107">If `enumerateWeakReferences` is `true`, the `ppEnum` enumerator includes both strong references and weak references.</span></span> <span data-ttu-id="4b2d6-108">Se `enumerateWeakReferences` é `false`, o enumerador inclui somente referências fortes.</span><span class="sxs-lookup"><span data-stu-id="4b2d6-108">If `enumerateWeakReferences` is `false`, the enumerator includes only strong references.</span></span>  
  
 `ppEnum`  
 <span data-ttu-id="4b2d6-109">[out] Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a ser coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="4b2d6-109">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4b2d6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="4b2d6-110">Remarks</span></span>  
 <span data-ttu-id="4b2d6-111">Esse método fornece uma maneira de determinar a cadeia de raiz no total de qualquer objeto gerenciado em um processo e pode ser usado para determinar por que um objeto ainda está ativo.</span><span class="sxs-lookup"><span data-stu-id="4b2d6-111">This method provides a way to determine the full rooting chain for any managed object in a process and can be used to determine why an object is still alive.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b2d6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4b2d6-112">Requirements</span></span>  
 <span data-ttu-id="4b2d6-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4b2d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b2d6-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4b2d6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4b2d6-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4b2d6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4b2d6-116">**Versões do .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b2d6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b2d6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4b2d6-117">See Also</span></span>  
 [<span data-ttu-id="4b2d6-118">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="4b2d6-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="4b2d6-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4b2d6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
