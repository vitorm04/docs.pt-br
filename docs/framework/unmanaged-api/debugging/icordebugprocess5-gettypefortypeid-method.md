---
title: Método ICorDebugProcess5::GetTypeForTypeID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: ea7f7a9d4589e4f08b1b1e20b4d073bb5f822714
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212757"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="a06ac-102">Método ICorDebugProcess5::GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="a06ac-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="a06ac-103">Converte um identificador de tipo em um valor ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a06ac-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a06ac-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a06ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a06ac-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a06ac-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a06ac-106">no O identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="a06ac-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="a06ac-107">fora Um ponteiro para o endereço de um objeto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="a06ac-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a06ac-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="a06ac-108">Remarks</span></span>  
 <span data-ttu-id="a06ac-109">Em alguns casos, os métodos que retornam um identificador de tipo podem retornar um `COR_TYPEID` valor nulo.</span><span class="sxs-lookup"><span data-stu-id="a06ac-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="a06ac-110">Se esse valor for passado como o `id` argumento, o `GetTypeForTypeID` método falhará e retornará `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="a06ac-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a06ac-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a06ac-111">Requirements</span></span>  
 <span data-ttu-id="a06ac-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a06ac-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a06ac-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a06ac-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a06ac-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a06ac-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a06ac-115">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a06ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06ac-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="a06ac-116">See also</span></span>

- [<span data-ttu-id="a06ac-117">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="a06ac-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a06ac-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a06ac-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
