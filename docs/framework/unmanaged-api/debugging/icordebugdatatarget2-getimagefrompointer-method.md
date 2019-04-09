---
title: Método ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5dab9183075f563f52a4fc982eda5cb172556554
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154369"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="04ffe-102">Método ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="04ffe-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="04ffe-103">Retorna o endereço base do módulo e o tamanho de um endereço no módulo.</span><span class="sxs-lookup"><span data-stu-id="04ffe-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04ffe-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04ffe-104">Syntax</span></span>  
  
```  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,   
   [out] CORDB_ADDRESS *pImageBase,   
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04ffe-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04ffe-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="04ffe-106">Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa um endereço em um módulo.</span><span class="sxs-lookup"><span data-stu-id="04ffe-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="04ffe-107">[out] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="04ffe-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="04ffe-108">Um ponteiro para o tamanho do módulo.</span><span class="sxs-lookup"><span data-stu-id="04ffe-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04ffe-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="04ffe-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="04ffe-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04ffe-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04ffe-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04ffe-111">Requirements</span></span>  
 <span data-ttu-id="04ffe-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04ffe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04ffe-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04ffe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04ffe-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04ffe-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="04ffe-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="04ffe-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="04ffe-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04ffe-116">See also</span></span>

- [<span data-ttu-id="04ffe-117">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="04ffe-117">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="04ffe-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="04ffe-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
