---
title: Método ICorDebugEval2::NewParameterizedArray
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedArray
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type:
- apiref
ms.openlocfilehash: 9476bcc9706e89fd3d7e0abc14031f70a0aa0ad0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084831"
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="a33c9-102">Método ICorDebugEval2::NewParameterizedArray</span><span class="sxs-lookup"><span data-stu-id="a33c9-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="a33c9-103">Aloca uma nova matriz do tipo e das dimensões do elemento especificado.</span><span class="sxs-lookup"><span data-stu-id="a33c9-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a33c9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a33c9-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a33c9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a33c9-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="a33c9-106">no Um ponteiro para um objeto ICorDebugType que representa o tipo de elemento armazenado na matriz.</span><span class="sxs-lookup"><span data-stu-id="a33c9-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="a33c9-107">no O número de dimensões da matriz.</span><span class="sxs-lookup"><span data-stu-id="a33c9-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="a33c9-108">No .NET Framework versão 2,0, esse valor deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="a33c9-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="a33c9-109">no O tamanho, em bytes, de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="a33c9-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="a33c9-110">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="a33c9-110">[in] Optional.</span></span> <span data-ttu-id="a33c9-111">O limite inferior de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="a33c9-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="a33c9-112">Se esse valor for omitido, um limite inferior de zero será assumido para cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="a33c9-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a33c9-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="a33c9-113">Remarks</span></span>  
 <span data-ttu-id="a33c9-114">Os elementos da matriz podem ser instâncias de um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="a33c9-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="a33c9-115">A matriz é sempre criada no domínio do aplicativo no qual o thread está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="a33c9-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="a33c9-116">No .NET Framework 2,0, o valor de `rank` deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="a33c9-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a33c9-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a33c9-117">Requirements</span></span>  
 <span data-ttu-id="a33c9-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a33c9-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a33c9-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a33c9-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a33c9-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a33c9-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a33c9-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a33c9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
