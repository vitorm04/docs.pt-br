---
title: "Método ICorDebugHeapValue2::CreateHandle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue2.CreateHandle
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue2::CreateHandle
helpviewer_keywords:
- CreateHandle method [.NET Framework debugging]
- ICorDebugHeapValue2::CreateHandle method [.NET Framework debugging]
ms.assetid: fbc418e8-fa22-420d-84ec-e0e1800db041
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7feef9af174a63976729f91b5a0b4967fea55b23
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="df043-102">Método ICorDebugHeapValue2::CreateHandle</span><span class="sxs-lookup"><span data-stu-id="df043-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="df043-103">Cria um identificador do tipo especificado para o valor de heap representado por esse objeto em ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="df043-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df043-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df043-104">Syntax</span></span>  
  
```  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df043-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df043-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="df043-106">[in] Um valor da enumeração CorDebugHandleType que especifica o tipo de identificador a ser criado.</span><span class="sxs-lookup"><span data-stu-id="df043-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="df043-107">[out] Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa o novo identificador para esse valor de heap.</span><span class="sxs-lookup"><span data-stu-id="df043-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df043-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="df043-108">Remarks</span></span>  
 <span data-ttu-id="df043-109">O identificador será criado no domínio do aplicativo que está associado com o valor de heap e se tornarão inválido se o domínio de aplicativo seja descarregado.</span><span class="sxs-lookup"><span data-stu-id="df043-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="df043-110">Várias chamadas a essa função para o mesmo valor de heap criará vários identificadores.</span><span class="sxs-lookup"><span data-stu-id="df043-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="df043-111">Identificadores de afetam o desempenho do coletor de lixo, o depurador deve limitar automaticamente para um número relativamente pequeno de identificadores (aproximadamente 256) que estão ativos por vez.</span><span class="sxs-lookup"><span data-stu-id="df043-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df043-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df043-112">Requirements</span></span>  
 <span data-ttu-id="df043-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df043-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df043-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df043-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df043-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df043-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df043-116">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df043-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
