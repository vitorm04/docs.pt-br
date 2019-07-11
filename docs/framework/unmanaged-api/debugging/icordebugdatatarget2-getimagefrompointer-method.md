---
title: Método ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5656bf28d92030ed8d8271d795e41f881932a73
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750213"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="953b1-102">Método ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="953b1-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="953b1-103">Retorna o endereço base do módulo e o tamanho de um endereço no módulo.</span><span class="sxs-lookup"><span data-stu-id="953b1-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="953b1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="953b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="953b1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="953b1-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="953b1-106">Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa um endereço em um módulo.</span><span class="sxs-lookup"><span data-stu-id="953b1-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="953b1-107">[out] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="953b1-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="953b1-108">Um ponteiro para o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="953b1-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="953b1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="953b1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="953b1-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="953b1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="953b1-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="953b1-111">Requirements</span></span>  
 <span data-ttu-id="953b1-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="953b1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="953b1-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="953b1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="953b1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="953b1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="953b1-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="953b1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953b1-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="953b1-116">See also</span></span>

- [<span data-ttu-id="953b1-117">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="953b1-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="953b1-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="953b1-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
