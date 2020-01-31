---
title: Método ICorDebugProcess5::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetObject method [.NET Framework debugging]
ms.assetid: c8111502-5a20-447f-9dc2-76e8acd7ed5a
topic_type:
- apiref
ms.openlocfilehash: 540ca78c5548d4fbdd3338671ea02314736f15cd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792359"
---
# <a name="icordebugprocess5getobject-method"></a><span data-ttu-id="d5c3e-102">Método ICorDebugProcess5::GetObject</span><span class="sxs-lookup"><span data-stu-id="d5c3e-102">ICorDebugProcess5::GetObject Method</span></span>
<span data-ttu-id="d5c3e-103">Converte um endereço de objeto em um objeto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="d5c3e-103">Converts an object address to an "ICorDebugObjectValue" object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5c3e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d5c3e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObject(  
    [in] CORDB_ADDRESS addr,   
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5c3e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d5c3e-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="d5c3e-106">no O endereço do objeto.</span><span class="sxs-lookup"><span data-stu-id="d5c3e-106">[in] The object address.</span></span>  
  
 `ppObject`  
 <span data-ttu-id="d5c3e-107">fora Um ponteiro para o endereço de um objeto "ICorDebugObjectValue".</span><span class="sxs-lookup"><span data-stu-id="d5c3e-107">[out] A pointer to the address of an  "ICorDebugObjectValue" object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5c3e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="d5c3e-108">Remarks</span></span>  
 <span data-ttu-id="d5c3e-109">Se `addr` não apontar para um objeto gerenciado válido, o método `GetObject` retornará `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="d5c3e-109">If `addr` does not point to a valid managed object, the `GetObject` method returns `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5c3e-110">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d5c3e-110">Requirements</span></span>  
 <span data-ttu-id="d5c3e-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5c3e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5c3e-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d5c3e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5c3e-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d5c3e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5c3e-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5c3e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5c3e-115">Veja também</span><span class="sxs-lookup"><span data-stu-id="d5c3e-115">See also</span></span>

- [<span data-ttu-id="d5c3e-116">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="d5c3e-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="d5c3e-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d5c3e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
