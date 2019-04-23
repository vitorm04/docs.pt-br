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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeb4ad1dffe4553b243b5168037aea8b68f8244b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59222049"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="818b8-102">Método ICorDebugProcess5::GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="818b8-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="818b8-103">Converte um identificador de tipo em um valor de ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="818b8-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="818b8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="818b8-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="818b8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="818b8-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="818b8-106">[in] O identificador de tipo.</span><span class="sxs-lookup"><span data-stu-id="818b8-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="818b8-107">[out] Um ponteiro para o endereço de um objeto ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="818b8-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="818b8-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="818b8-108">Remarks</span></span>  
 <span data-ttu-id="818b8-109">Em alguns casos, os métodos que retornam um identificador de tipo podem retornar um valor nulo `COR_TYPEID` valor.</span><span class="sxs-lookup"><span data-stu-id="818b8-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="818b8-110">Se esse valor é passado como o `id` argumento, o `GetTypeForTypeID` método falhará e retornará `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="818b8-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="818b8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="818b8-111">Requirements</span></span>  
 <span data-ttu-id="818b8-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="818b8-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="818b8-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="818b8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="818b8-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="818b8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="818b8-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="818b8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818b8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="818b8-116">See also</span></span>

- [<span data-ttu-id="818b8-117">Interface ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="818b8-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="818b8-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="818b8-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
