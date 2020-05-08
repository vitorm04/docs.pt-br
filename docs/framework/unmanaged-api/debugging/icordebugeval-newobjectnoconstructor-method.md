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
ms.openlocfilehash: d41216eb7da57d29d67ce17372f746328204649e
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976168"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="a1fba-102">Método ICorDebugEval::NewObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="a1fba-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="a1fba-103">Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor.</span><span class="sxs-lookup"><span data-stu-id="a1fba-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="a1fba-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="a1fba-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a1fba-105">Use [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a1fba-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1fba-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1fba-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1fba-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1fba-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="a1fba-108">no Ponteiro para um objeto ICorDebugClass que representa o tipo de objeto a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="a1fba-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1fba-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1fba-109">Requirements</span></span>  
 <span data-ttu-id="a1fba-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1fba-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1fba-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1fba-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1fba-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1fba-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1fba-113">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="a1fba-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fba-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1fba-114">See also</span></span>

- [<span data-ttu-id="a1fba-115">Método NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="a1fba-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
