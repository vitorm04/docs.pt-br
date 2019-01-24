---
title: Método ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b2d6db83f78cb76181c0b54a8e6f4157e51130b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648830"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="6b9c4-102">Método ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="6b9c4-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="6b9c4-103">Retorna o caminho de um módulo de endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="6b9c4-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b9c4-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b9c4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b9c4-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="6b9c4-106">[in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="6b9c4-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6b9c4-107">[in] O número de caracteres no buffer que receberá o caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="6b9c4-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6b9c4-108">[out] Um ponteiro para o número de caracteres gravados para o buffer `szName`.</span><span class="sxs-lookup"><span data-stu-id="6b9c4-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6b9c4-109">[out] O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="6b9c4-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b9c4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6b9c4-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6b9c4-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6b9c4-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b9c4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b9c4-112">Requirements</span></span>  
 <span data-ttu-id="6b9c4-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b9c4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b9c4-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b9c4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b9c4-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b9c4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b9c4-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b9c4-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9c4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b9c4-117">See also</span></span>
- [<span data-ttu-id="6b9c4-118">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="6b9c4-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="6b9c4-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="6b9c4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
