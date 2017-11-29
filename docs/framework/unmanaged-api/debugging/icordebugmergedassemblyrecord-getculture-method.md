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
ms.openlocfilehash: 7791491a050e31d8d6c5dfb6ef9ffe209921753d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="fa765-102">Método ICorDebugMergedAssemblyRecord::GetCulture</span><span class="sxs-lookup"><span data-stu-id="fa765-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="fa765-103">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="fa765-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa765-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa765-104">Syntax</span></span>  
  
```  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa765-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa765-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="fa765-106">[in] O número de caracteres a `szCulture` buffer.</span><span class="sxs-lookup"><span data-stu-id="fa765-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="fa765-107">[out] O número de caracteres gravados o `szCulture` buffer.</span><span class="sxs-lookup"><span data-stu-id="fa765-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="fa765-108">[out] Uma matriz de caracteres que contém o nome de cultura.</span><span class="sxs-lookup"><span data-stu-id="fa765-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa765-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa765-109">Remarks</span></span>  
 <span data-ttu-id="fa765-110">O nome de cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura do inglês (Estados Unidos)) ou "neutral" (para uma cultura neutra).</span><span class="sxs-lookup"><span data-stu-id="fa765-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fa765-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fa765-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa765-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa765-112">Requirements</span></span>  
 <span data-ttu-id="fa765-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa765-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa765-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa765-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa765-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa765-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa765-116">**Versões do .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa765-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa765-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa765-117">See Also</span></span>  
 [<span data-ttu-id="fa765-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="fa765-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 [<span data-ttu-id="fa765-119">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="fa765-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
