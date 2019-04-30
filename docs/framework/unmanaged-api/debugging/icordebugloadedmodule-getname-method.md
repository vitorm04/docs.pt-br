---
title: Método ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bf09c01d24315c3f239911326f1844a0b2cc101
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946257"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="29ce4-102">Método ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="29ce4-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="29ce4-103">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="29ce4-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ce4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29ce4-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29ce4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29ce4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="29ce4-106">[in] O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="29ce4-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="29ce4-107">[out] Um ponteiro para o número de caracteres gravados, na verdade, o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="29ce4-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="29ce4-108">[out] Uma matriz de caracteres que contêm o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="29ce4-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29ce4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="29ce4-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29ce4-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="29ce4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ce4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29ce4-111">Requirements</span></span>  
 <span data-ttu-id="29ce4-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29ce4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29ce4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29ce4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29ce4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29ce4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29ce4-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29ce4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29ce4-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29ce4-116">See also</span></span>

- [<span data-ttu-id="29ce4-117">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="29ce4-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="29ce4-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="29ce4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
