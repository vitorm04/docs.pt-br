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
ms.openlocfilehash: 5ff378602fc7338263ef49aee6802d2138bab9d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413166"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="26d9e-102">Método ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="26d9e-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="26d9e-103">Aloca uma nova instância de objeto e chama o método de construtor especificado.</span><span class="sxs-lookup"><span data-stu-id="26d9e-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="26d9e-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="26d9e-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="26d9e-105">Use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="26d9e-105">Use [ICorDebugEval2::NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26d9e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26d9e-106">Syntax</span></span>  
  
```  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26d9e-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26d9e-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="26d9e-108">[in] O construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="26d9e-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="26d9e-109">[in] O tamanho do `ppArgs` matriz.</span><span class="sxs-lookup"><span data-stu-id="26d9e-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="26d9e-110">[in] Uma matriz de objetos ICorDebugValue, cada um deles representa um argumento a ser passado para o construtor.</span><span class="sxs-lookup"><span data-stu-id="26d9e-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26d9e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="26d9e-111">Requirements</span></span>  
 <span data-ttu-id="26d9e-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26d9e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26d9e-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="26d9e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26d9e-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="26d9e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26d9e-115">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="26d9e-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26d9e-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26d9e-116">See Also</span></span>  
 [<span data-ttu-id="26d9e-117">Método NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="26d9e-117">NewParameterizedObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)
