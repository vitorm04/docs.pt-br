---
title: Método ICorDebugProcess6::GetCode
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: fc7fecc3f523d7992bd57e2f7d485648caa6df8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123476"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="6a38f-102">Método ICorDebugProcess6::GetCode</span><span class="sxs-lookup"><span data-stu-id="6a38f-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="6a38f-103">Obtém informações sobre o código gerenciado em um endereço de código em particular.</span><span class="sxs-lookup"><span data-stu-id="6a38f-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a38f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a38f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6a38f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6a38f-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="6a38f-106">no Um valor de [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que especifica o endereço inicial do segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6a38f-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="6a38f-107">fora Um ponteiro para o endereço de um objeto "ICorDebugCode" que representa um segmento de código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="6a38f-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6a38f-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a38f-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6a38f-109">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6a38f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a38f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6a38f-110">Requirements</span></span>  
 <span data-ttu-id="6a38f-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a38f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a38f-112">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a38f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a38f-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a38f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a38f-114">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a38f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a38f-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a38f-115">See also</span></span>

- [<span data-ttu-id="6a38f-116">Interface ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="6a38f-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="6a38f-117">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6a38f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
