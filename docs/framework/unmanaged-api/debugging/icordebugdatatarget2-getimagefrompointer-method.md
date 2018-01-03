---
title: "Método ICorDebugDataTarget2::GetImageFromPointer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cfe25a90fb2084c1f58eff5b42e24b15decb0163
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="399a9-102">Método ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="399a9-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="399a9-103">Retorna o endereço base do módulo e o tamanho de um endereço no módulo.</span><span class="sxs-lookup"><span data-stu-id="399a9-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="399a9-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="399a9-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="399a9-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="399a9-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="399a9-106">Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa um endereço em um módulo.</span><span class="sxs-lookup"><span data-stu-id="399a9-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="399a9-107">[out] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="399a9-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="399a9-108">Um ponteiro para o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="399a9-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="399a9-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="399a9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="399a9-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="399a9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="399a9-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="399a9-111">Requirements</span></span>  
 <span data-ttu-id="399a9-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="399a9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="399a9-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="399a9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="399a9-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="399a9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="399a9-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="399a9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399a9-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="399a9-116">See Also</span></span>  
 [<span data-ttu-id="399a9-117">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="399a9-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="399a9-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="399a9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
