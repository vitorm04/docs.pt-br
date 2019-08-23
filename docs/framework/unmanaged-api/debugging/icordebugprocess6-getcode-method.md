---
title: Método ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d896cc4316c2de6fa1cb0bacc9ff8b1f3713129
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967552"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="92186-102">Método ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="92186-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="92186-103">Obtém informações sobre o código gerenciado em um endereço de código em particular.</span><span class="sxs-lookup"><span data-stu-id="92186-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92186-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92186-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92186-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92186-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="92186-106">no Um valor de [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que especifica o endereço inicial do segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92186-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="92186-107">fora Um ponteiro para o endereço de um objeto "ICorDebugCode" que representa um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92186-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92186-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="92186-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92186-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="92186-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92186-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92186-110">Requirements</span></span>  
 <span data-ttu-id="92186-111">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92186-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92186-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92186-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92186-113">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92186-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92186-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92186-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92186-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92186-115">See also</span></span>

- [<span data-ttu-id="92186-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="92186-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="92186-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="92186-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
