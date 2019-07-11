---
title: Método ICorDebugMergedAssemblyRecord::GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0472a52d0893bfd487cd6daa6548ec1ce0c44a9b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762212"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="5b136-102">Método ICorDebugMergedAssemblyRecord::GetCulture</span><span class="sxs-lookup"><span data-stu-id="5b136-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="5b136-103">Obtém a cadeia de caracteres de nome de cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="5b136-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b136-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b136-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b136-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5b136-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="5b136-106">[in] O número de caracteres no `szCulture` buffer.</span><span class="sxs-lookup"><span data-stu-id="5b136-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="5b136-107">[out] O número de caracteres gravados, na verdade, o `szCulture` buffer.</span><span class="sxs-lookup"><span data-stu-id="5b136-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="5b136-108">[out] Uma matriz de caracteres que contém o nome da cultura.</span><span class="sxs-lookup"><span data-stu-id="5b136-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5b136-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="5b136-109">Remarks</span></span>  
 <span data-ttu-id="5b136-110">O nome de cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura do inglês (Estados Unidos)) ou "neutral" (para uma cultura neutra).</span><span class="sxs-lookup"><span data-stu-id="5b136-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b136-111">Esse método só está disponível com o .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5b136-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b136-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b136-112">Requirements</span></span>  
 <span data-ttu-id="5b136-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b136-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b136-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5b136-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5b136-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b136-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b136-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b136-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b136-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b136-117">See also</span></span>

- [<span data-ttu-id="5b136-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="5b136-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="5b136-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="5b136-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
