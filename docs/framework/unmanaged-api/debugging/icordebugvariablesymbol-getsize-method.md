---
title: 'Método ICorDebugVariableSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 61dad9522f9171166ca56a97e68b9a149d35e49a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120999"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="d7828-102">Método ICorDebugVariableSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="d7828-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="d7828-103">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="d7828-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7828-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7828-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7828-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d7828-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="d7828-106">Um ponteiro para um inteiro sem sinal de 32 bits contendo o tamanho da variável.</span><span class="sxs-lookup"><span data-stu-id="d7828-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7828-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7828-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7828-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d7828-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7828-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7828-109">Requirements</span></span>  
 <span data-ttu-id="d7828-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7828-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7828-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7828-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7828-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7828-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7828-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7828-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7828-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7828-114">See also</span></span>

- [<span data-ttu-id="d7828-115">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="d7828-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d7828-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d7828-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
