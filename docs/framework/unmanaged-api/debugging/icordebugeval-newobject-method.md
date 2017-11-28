---
title: "Método ICorDebugEval::NewObject"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewObject
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e478f057b3c319d099b0156188f3d1e23bb82e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="a1eb5-102">Método ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="a1eb5-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="a1eb5-103">Aloca uma nova instância de objeto e chama o método de construtor especificado.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="a1eb5-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="a1eb5-105">Use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1eb5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1eb5-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a1eb5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a1eb5-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="a1eb5-108">[in] O construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="a1eb5-109">[in] O tamanho do `ppArgs` matriz.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="a1eb5-110">[in] Uma matriz de objetos ICorDebugValue, cada um deles representa um argumento a ser passado para o construtor.</span><span class="sxs-lookup"><span data-stu-id="a1eb5-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1eb5-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1eb5-111">Requirements</span></span>  
 <span data-ttu-id="a1eb5-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1eb5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1eb5-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1eb5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1eb5-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1eb5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1eb5-115">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="a1eb5-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1eb5-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1eb5-116">See Also</span></span>  
 [<span data-ttu-id="a1eb5-117">Método NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="a1eb5-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
