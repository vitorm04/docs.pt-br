---
title: Método ICorDebugEval::NewObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6846b866fd47674ca6b5fd187b580fd28e080fd0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61995924"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="b6881-102">Método ICorDebugEval::NewObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="b6881-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="b6881-103">Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor.</span><span class="sxs-lookup"><span data-stu-id="b6881-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="b6881-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="b6881-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b6881-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b6881-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6881-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6881-106">Syntax</span></span>  
  
```  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6881-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6881-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="b6881-108">[in] Ponteiro para um objeto de ICorDebugClass que representa o tipo de objeto a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="b6881-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6881-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6881-109">Requirements</span></span>  
 <span data-ttu-id="b6881-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6881-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6881-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6881-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6881-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6881-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6881-113">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="b6881-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6881-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6881-114">See also</span></span>

- [<span data-ttu-id="b6881-115">Método NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="b6881-115">NewParameterizedObjectNoConstructor Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)
