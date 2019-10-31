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
ms.openlocfilehash: b9eab1274f2d0ad562c0dec6adeddb85c6cfc458
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138386"
---
# <a name="icordebugheapvalue2createhandle-method"></a><span data-ttu-id="64a85-102">Método ICorDebugHeapValue2::CreateHandle</span><span class="sxs-lookup"><span data-stu-id="64a85-102">ICorDebugHeapValue2::CreateHandle Method</span></span>
<span data-ttu-id="64a85-103">Cria um identificador do tipo especificado para o valor de heap representado por esse objeto ICorDebugHeapValue2.</span><span class="sxs-lookup"><span data-stu-id="64a85-103">Creates a handle of the specified type for the heap value represented by this ICorDebugHeapValue2 object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64a85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="64a85-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateHandle (  
    [in] CorDebugHandleType      type,   
    [out] ICorDebugHandleValue   **ppHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="64a85-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="64a85-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="64a85-106">no Um valor da Enumeração CorDebugHandleType que especifica o tipo de identificador a ser criado.</span><span class="sxs-lookup"><span data-stu-id="64a85-106">[in] A value of the CorDebugHandleType enumeration that specifies the type of handle to be created.</span></span>  
  
 `ppHandle`  
 <span data-ttu-id="64a85-107">fora Um ponteiro para o endereço de um objeto ICorDebugHandleValue que representa o novo identificador para esse valor de heap.</span><span class="sxs-lookup"><span data-stu-id="64a85-107">[out] A pointer to the address of an ICorDebugHandleValue object that represents the new handle for this heap value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64a85-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="64a85-108">Remarks</span></span>  
 <span data-ttu-id="64a85-109">O identificador será criado no domínio do aplicativo que está associado ao valor de heap e se tornará inválido se o domínio do aplicativo for descarregado.</span><span class="sxs-lookup"><span data-stu-id="64a85-109">The handle will be created in the application domain that is associated with the heap value, and will become invalid if the application domain gets unloaded.</span></span>  
  
 <span data-ttu-id="64a85-110">Várias chamadas para essa função para o mesmo valor de heap criarão vários identificadores.</span><span class="sxs-lookup"><span data-stu-id="64a85-110">Multiple calls to this function for the same heap value will create multiple handles.</span></span> <span data-ttu-id="64a85-111">Como os identificadores afetam o desempenho do coletor de lixo, o depurador deve se limitar a um número relativamente pequeno de identificadores (cerca de 256) que estejam ativos por vez.</span><span class="sxs-lookup"><span data-stu-id="64a85-111">Because handles affect the performance of the garbage collector, the debugger should limit itself to a relatively small number of handles (about 256) that are active at a time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64a85-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="64a85-112">Requirements</span></span>  
 <span data-ttu-id="64a85-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64a85-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64a85-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="64a85-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="64a85-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64a85-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64a85-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64a85-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
