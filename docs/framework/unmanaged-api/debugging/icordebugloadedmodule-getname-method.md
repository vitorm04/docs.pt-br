---
title: Método ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e97c7c793df389dd6a8f670e985a9c9384eab639
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703738"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="308a7-102">Método ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="308a7-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="308a7-103">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="308a7-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="308a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="308a7-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="308a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="308a7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="308a7-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="308a7-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="308a7-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="308a7-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="308a7-108">[out] Uma matriz de caracteres que contêm o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="308a7-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="308a7-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="308a7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="308a7-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="308a7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="308a7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="308a7-111">Requirements</span></span>  
 <span data-ttu-id="308a7-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="308a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="308a7-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="308a7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="308a7-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="308a7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="308a7-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="308a7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="308a7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="308a7-116">See also</span></span>
- [<span data-ttu-id="308a7-117">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="308a7-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="308a7-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="308a7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
