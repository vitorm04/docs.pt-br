---
title: "Método ICorDebugMergedAssemblyRecord::GetCulture"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7963d311707d12aa697c606605f9a34b6f65d1eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="cdca0-102">Método ICorDebugMergedAssemblyRecord::GetCulture</span><span class="sxs-lookup"><span data-stu-id="cdca0-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="cdca0-103">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="cdca0-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdca0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cdca0-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cdca0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cdca0-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="cdca0-106">[in] O número de caracteres a `szCulture` buffer.</span><span class="sxs-lookup"><span data-stu-id="cdca0-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="cdca0-107">[out] O número de caracteres gravados o `szCulture` buffer.</span><span class="sxs-lookup"><span data-stu-id="cdca0-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="cdca0-108">[out] Uma matriz de caracteres que contém o nome de cultura.</span><span class="sxs-lookup"><span data-stu-id="cdca0-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdca0-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="cdca0-109">Remarks</span></span>  
 <span data-ttu-id="cdca0-110">O nome de cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura do inglês (Estados Unidos)) ou "neutral" (para uma cultura neutra).</span><span class="sxs-lookup"><span data-stu-id="cdca0-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cdca0-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cdca0-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdca0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cdca0-112">Requirements</span></span>  
 <span data-ttu-id="cdca0-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdca0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdca0-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cdca0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdca0-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cdca0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdca0-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdca0-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdca0-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cdca0-117">See Also</span></span>  
 [<span data-ttu-id="cdca0-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="cdca0-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="cdca0-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cdca0-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
