---
title: Método ICorDebugStaticFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a30778a287b4115df552444549a92c006288005
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760756"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="2c3a7-102">Método ICorDebugStaticFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="2c3a7-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="2c3a7-103">Obtém o tamanho em bytes do campo estático.</span><span class="sxs-lookup"><span data-stu-id="2c3a7-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c3a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2c3a7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c3a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2c3a7-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="2c3a7-106">[out] Um ponteiro para o comprimento do campo.</span><span class="sxs-lookup"><span data-stu-id="2c3a7-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c3a7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="2c3a7-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2c3a7-108">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2c3a7-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c3a7-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2c3a7-109">Requirements</span></span>  
 <span data-ttu-id="2c3a7-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c3a7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c3a7-111">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c3a7-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c3a7-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c3a7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c3a7-113">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c3a7-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c3a7-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2c3a7-114">See also</span></span>

- [<span data-ttu-id="2c3a7-115">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="2c3a7-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="2c3a7-116">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2c3a7-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
