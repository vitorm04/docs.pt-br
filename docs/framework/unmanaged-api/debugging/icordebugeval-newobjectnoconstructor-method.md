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
ms.openlocfilehash: 45efa1939813a319e996a72fef62ada167b877c2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788694"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="60e9f-102">Método ICorDebugEval::NewObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="60e9f-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>
<span data-ttu-id="60e9f-103">Aloca uma nova instância de objeto do tipo especificado, sem tentar chamar um método de construtor.</span><span class="sxs-lookup"><span data-stu-id="60e9f-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="60e9f-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="60e9f-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="60e9f-105">Use [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="60e9f-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60e9f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60e9f-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60e9f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="60e9f-107">Parameters</span></span>  
 `pClass`  
 <span data-ttu-id="60e9f-108">no Ponteiro para um objeto ICorDebugClass que representa o tipo de objeto a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="60e9f-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60e9f-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="60e9f-109">Requirements</span></span>  
 <span data-ttu-id="60e9f-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60e9f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60e9f-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60e9f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60e9f-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60e9f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60e9f-113">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="60e9f-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60e9f-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="60e9f-114">See also</span></span>

- [<span data-ttu-id="60e9f-115">Método NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="60e9f-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
