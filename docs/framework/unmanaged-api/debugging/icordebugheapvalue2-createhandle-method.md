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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 078dfd7162c250f0279b8bc372aeb39662aa0119
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779880"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="5ced3-102">Método ICorDebugHeapValue2::CreateHandle</span><span class="sxs-lookup"><span data-stu-id="5ced3-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="5ced3-103">Cria um identificador do tipo especificado para o valor de heap representado por esse objeto ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="5ced3-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ced3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ced3-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ced3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ced3-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="5ced3-106">[in] Um valor de enumeração CorDebugHandleType que especifica o tipo de identificador a ser criado.</span><span class="sxs-lookup"><span data-stu-id="5ced3-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="5ced3-107">[out] Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa o novo identificador para esse valor de heap.</span><span class="sxs-lookup"><span data-stu-id="5ced3-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ced3-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ced3-108">Remarks</span></span>  
 <span data-ttu-id="5ced3-109">O identificador será criado no domínio do aplicativo que está associado com o valor de heap e se tornará inválido caso se o domínio do aplicativo seja descarregado.</span><span class="sxs-lookup"><span data-stu-id="5ced3-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="5ced3-110">Várias chamadas para essa função para o mesmo valor de heap criará vários identificadores.</span><span class="sxs-lookup"><span data-stu-id="5ced3-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="5ced3-111">Como identificadores de afetam o desempenho do coletor de lixo, o depurador deve se limitar a um número relativamente pequeno de identificadores (cerca de 256) que estão ativos por vez.</span><span class="sxs-lookup"><span data-stu-id="5ced3-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ced3-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ced3-112">Requirements</span></span>  
 <span data-ttu-id="5ced3-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ced3-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ced3-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ced3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ced3-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ced3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ced3-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ced3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
