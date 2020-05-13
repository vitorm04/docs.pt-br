---
title: 'Método ICorDebugStaticFieldSymbol:: GetSize'
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: e36c94bf411e75f915cca86aee74cdf161674d25
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379406"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="9495a-102">Método ICorDebugStaticFieldSymbol:: GetSize</span><span class="sxs-lookup"><span data-stu-id="9495a-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="9495a-103">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="9495a-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9495a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9495a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9495a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9495a-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="9495a-106">fora Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="9495a-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9495a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="9495a-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9495a-108">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9495a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9495a-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9495a-109">Requirements</span></span>  
 <span data-ttu-id="9495a-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9495a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9495a-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9495a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9495a-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9495a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9495a-113">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9495a-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9495a-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="9495a-114">See also</span></span>

- [<span data-ttu-id="9495a-115">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="9495a-115">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="9495a-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9495a-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
