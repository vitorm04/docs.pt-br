---
title: "Método ICorDebugLoadedModule::GetName"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: aee475dfc425eea32ce4a1e5b4a081593574ba64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="eb345-102">Método ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="eb345-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="eb345-103">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="eb345-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb345-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eb345-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb345-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="eb345-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="eb345-106">[in] O número de caracteres a `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="eb345-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="eb345-107">[out] Um ponteiro para o número de caracteres gravados o `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="eb345-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="eb345-108">[out] Uma matriz de caracteres que contém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="eb345-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb345-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="eb345-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eb345-110">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="eb345-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb345-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="eb345-111">Requirements</span></span>  
 <span data-ttu-id="eb345-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb345-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb345-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eb345-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb345-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb345-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb345-115">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb345-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb345-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eb345-116">See Also</span></span>  
 [<span data-ttu-id="eb345-117">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="eb345-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="eb345-118">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="eb345-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
