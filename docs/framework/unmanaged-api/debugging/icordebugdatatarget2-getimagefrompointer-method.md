---
title: Método ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178912"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="2a9ad-102">Método ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="2a9ad-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="2a9ad-103">Retorna o endereço base do módulo e o tamanho de um endereço no módulo.</span><span class="sxs-lookup"><span data-stu-id="2a9ad-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a9ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2a9ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a9ad-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2a9ad-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="2a9ad-106">Um [valor CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa um endereço em um módulo.</span><span class="sxs-lookup"><span data-stu-id="2a9ad-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="2a9ad-107">[fora] Um [valor CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="2a9ad-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="2a9ad-108">Um ponteiro para o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="2a9ad-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2a9ad-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="2a9ad-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a9ad-110">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2a9ad-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a9ad-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2a9ad-111">Requirements</span></span>  
 <span data-ttu-id="2a9ad-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a9ad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a9ad-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2a9ad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2a9ad-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2a9ad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a9ad-115">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a9ad-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a9ad-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="2a9ad-116">See also</span></span>

- [<span data-ttu-id="2a9ad-117">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="2a9ad-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="2a9ad-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="2a9ad-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
