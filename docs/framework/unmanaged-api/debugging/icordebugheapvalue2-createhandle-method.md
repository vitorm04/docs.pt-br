---
title: Método ICorDebugHeapValue2::CreateHandle
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2.CreateHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type:
- apiref
ms.openlocfilehash: c7a1bf3cb10cbc8cdae2788b45e1badaf66a9dbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178873"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="cca4e-102">Método ICorDebugHeapValue2::CreateHandle</span><span class="sxs-lookup"><span data-stu-id="cca4e-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="cca4e-103">Cria uma alça do tipo especificado para o valor de pilha representado por este objeto ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="cca4e-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cca4e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cca4e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cca4e-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="cca4e-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="cca4e-106">[em] Um valor da enumeração CorDebugHandleType que especifica o tipo de alça a ser criada.</span><span class="sxs-lookup"><span data-stu-id="cca4e-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="cca4e-107">[fora] Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa a nova alça para este valor de pilha.</span><span class="sxs-lookup"><span data-stu-id="cca4e-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cca4e-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="cca4e-108">Remarks</span></span>  
 <span data-ttu-id="cca4e-109">A alça será criada no domínio do aplicativo que está associado ao valor de pilha e se tornará inválida se o domínio do aplicativo for descarregado.</span><span class="sxs-lookup"><span data-stu-id="cca4e-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="cca4e-110">Várias chamadas para esta função para o mesmo valor de pilha criarão várias alças.</span><span class="sxs-lookup"><span data-stu-id="cca4e-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="cca4e-111">Como as alças afetam o desempenho do coletor de lixo, o depurador deve limitar-se a um número relativamente pequeno de alças (cerca de 256) que estão ativas por vez.</span><span class="sxs-lookup"><span data-stu-id="cca4e-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cca4e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cca4e-112">Requirements</span></span>  
 <span data-ttu-id="cca4e-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cca4e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cca4e-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cca4e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cca4e-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cca4e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cca4e-116">**.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cca4e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
