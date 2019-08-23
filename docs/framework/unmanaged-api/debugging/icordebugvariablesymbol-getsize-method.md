---
title: 'Método ICorDebugVariableSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 782073968030d3dcdbbe49e0ed7732fe15c4a3bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968176"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="7bc17-102">Método ICorDebugVariableSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="7bc17-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="7bc17-103">Obtém o tamanho de uma variável em bytes.</span><span class="sxs-lookup"><span data-stu-id="7bc17-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bc17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bc17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bc17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7bc17-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="7bc17-106">Um ponteiro para um inteiro sem sinal de 32 bits contendo o tamanho da variável.</span><span class="sxs-lookup"><span data-stu-id="7bc17-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7bc17-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bc17-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7bc17-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7bc17-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bc17-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7bc17-109">Requirements</span></span>  
 <span data-ttu-id="7bc17-110">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bc17-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bc17-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bc17-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bc17-112">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bc17-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bc17-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bc17-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bc17-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7bc17-114">See also</span></span>

- [<span data-ttu-id="7bc17-115">Interface ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="7bc17-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="7bc17-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7bc17-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
