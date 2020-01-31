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
ms.openlocfilehash: 38cc98f1bfd966d1f764e43b30003a2bae66297d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793465"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="c4e5c-102">Método ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="c4e5c-102">ICorDebugEval::NewObject Method</span></span>
<span data-ttu-id="c4e5c-103">Aloca uma nova instância de objeto e chama o método de Construtor especificado.</span><span class="sxs-lookup"><span data-stu-id="c4e5c-103">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="c4e5c-104">Esse método é obsoleto no .NET Framework versão 2,0.</span><span class="sxs-lookup"><span data-stu-id="c4e5c-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="c4e5c-105">Use [ICorDebugEval2:: NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c4e5c-105">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4e5c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c4e5c-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4e5c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c4e5c-107">Parameters</span></span>  
 `pConstructor`  
 <span data-ttu-id="c4e5c-108">no O Construtor a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="c4e5c-108">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="c4e5c-109">no O tamanho da matriz de `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="c4e5c-109">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="c4e5c-110">no Uma matriz de objetos ICorDebugValue, cada um dos quais representa um argumento a ser passado para o construtor.</span><span class="sxs-lookup"><span data-stu-id="c4e5c-110">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4e5c-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="c4e5c-111">Requirements</span></span>  
 <span data-ttu-id="c4e5c-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4e5c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4e5c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4e5c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4e5c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4e5c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4e5c-115">**Versões do .NET Framework:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="c4e5c-115">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4e5c-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="c4e5c-116">See also</span></span>

- [<span data-ttu-id="c4e5c-117">Método NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="c4e5c-117">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
