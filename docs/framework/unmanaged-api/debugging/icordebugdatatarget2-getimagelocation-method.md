---
title: "Método ICorDebugDataTarget2::GetImageLocation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d35e35ecf4dfc62575e42a45a861ad685f3f26b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="6aa75-102">Método ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="6aa75-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="6aa75-103">Retorna o caminho de um módulo de endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="6aa75-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aa75-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6aa75-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6aa75-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6aa75-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="6aa75-106">[in] Um [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) valor que representa o endereço base do módulo.</span><span class="sxs-lookup"><span data-stu-id="6aa75-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="6aa75-107">[in] O número de caracteres no buffer que receberá o caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="6aa75-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6aa75-108">[out] Um ponteiro para o número de caracteres gravados para o buffer `szName`.</span><span class="sxs-lookup"><span data-stu-id="6aa75-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6aa75-109">[out] O caminho do módulo.</span><span class="sxs-lookup"><span data-stu-id="6aa75-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6aa75-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="6aa75-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6aa75-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6aa75-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aa75-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6aa75-112">Requirements</span></span>  
 <span data-ttu-id="6aa75-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aa75-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aa75-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6aa75-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aa75-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aa75-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aa75-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aa75-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aa75-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6aa75-117">See Also</span></span>  
 [<span data-ttu-id="6aa75-118">Interface ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="6aa75-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="6aa75-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="6aa75-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
