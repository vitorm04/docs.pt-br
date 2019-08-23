---
title: Método ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b046a5fcd514dde84e2f0f8c22ee23529ee906e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911462"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="22cdb-102">Método ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="22cdb-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="22cdb-103">Retorna o caminho de um módulo de endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="22cdb-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22cdb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22cdb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22cdb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22cdb-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="22cdb-106">no Um valor de [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="22cdb-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="22cdb-107">[in] O número de caracteres no buffer que receberá o caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="22cdb-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="22cdb-108">[out] Um ponteiro para o número de caracteres gravados para o buffer `szName`.</span><span class="sxs-lookup"><span data-stu-id="22cdb-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="22cdb-109">[out] O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="22cdb-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22cdb-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="22cdb-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22cdb-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="22cdb-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22cdb-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="22cdb-112">Requirements</span></span>  
 <span data-ttu-id="22cdb-113">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22cdb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22cdb-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22cdb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22cdb-115">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22cdb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22cdb-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22cdb-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22cdb-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22cdb-117">See also</span></span>

- [<span data-ttu-id="22cdb-118">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="22cdb-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="22cdb-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="22cdb-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
