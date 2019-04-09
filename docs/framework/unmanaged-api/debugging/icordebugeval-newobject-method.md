---
title: Método ICorDebugEval::NewObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c2d6a66eca080b480b508afea36c33b3e0aeec0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178224"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="bb52b-102">Método ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="bb52b-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="bb52b-103">Aloca uma nova instância de objeto e chama o método de construtor especificado.</span><span class="sxs-lookup"><span data-stu-id="bb52b-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="bb52b-104">Este método é obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="bb52b-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="bb52b-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="bb52b-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb52b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb52b-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb52b-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bb52b-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="bb52b-108">[in] O construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="bb52b-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="bb52b-109">[in] O tamanho do `ppArgs` matriz.</span><span class="sxs-lookup"><span data-stu-id="bb52b-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="bb52b-110">[in] Uma matriz de objetos ICorDebugValue, cada um deles representa um argumento a ser passado para o construtor.</span><span class="sxs-lookup"><span data-stu-id="bb52b-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb52b-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb52b-111">Requirements</span></span>  
 <span data-ttu-id="bb52b-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb52b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb52b-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb52b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb52b-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb52b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb52b-115">**Versões do .NET framework:** 1.1, 1.0</span><span class="sxs-lookup"><span data-stu-id="bb52b-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb52b-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb52b-116">See also</span></span>

- [<span data-ttu-id="bb52b-117">Método NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="bb52b-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
