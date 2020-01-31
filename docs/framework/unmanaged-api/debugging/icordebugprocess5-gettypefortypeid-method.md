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
ms.openlocfilehash: bb25c9235e4fcded5c230d2d417b9d41bbdd9b19
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792334"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="7a863-102">Método ICorDebugProcess5::GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="7a863-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="7a863-103">Converte um identificador de tipo em um valor ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="7a863-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a863-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a863-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a863-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7a863-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7a863-106">no O identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="7a863-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="7a863-107">fora Um ponteiro para o endereço de um objeto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="7a863-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a863-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a863-108">Remarks</span></span>  
 <span data-ttu-id="7a863-109">Em alguns casos, os métodos que retornam um identificador de tipo podem retornar um valor de `COR_TYPEID` nulo.</span><span class="sxs-lookup"><span data-stu-id="7a863-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="7a863-110">Se esse valor for passado como o argumento `id`, o método `GetTypeForTypeID` falhará e retornará `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="7a863-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a863-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7a863-111">Requirements</span></span>  
 <span data-ttu-id="7a863-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a863-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a863-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a863-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a863-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a863-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a863-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a863-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a863-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="7a863-116">See also</span></span>

- [<span data-ttu-id="7a863-117">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="7a863-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="7a863-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7a863-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
