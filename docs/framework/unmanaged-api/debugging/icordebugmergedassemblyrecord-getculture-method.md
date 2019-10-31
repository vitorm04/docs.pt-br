---
title: 'Método ICorDebugMergedAssemblyRecord:: getculture'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f39a1f17c80d27a38c0f2a8a516405f72c79bbcf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131422"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="1cc0f-102">Método ICorDebugMergedAssemblyRecord:: getculture</span><span class="sxs-lookup"><span data-stu-id="1cc0f-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="1cc0f-103">Obtém a cadeia de caracteres do nome da cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="1cc0f-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cc0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cc0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cc0f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cc0f-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="1cc0f-106">no O número de caracteres no buffer de `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="1cc0f-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="1cc0f-107">fora O número de caracteres realmente gravados no buffer de `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="1cc0f-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="1cc0f-108">fora Uma matriz de caracteres que contém o nome da cultura.</span><span class="sxs-lookup"><span data-stu-id="1cc0f-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cc0f-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cc0f-109">Remarks</span></span>  
 <span data-ttu-id="1cc0f-110">O nome da cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura em inglês (Estados Unidos)) ou "neutro" (para uma cultura neutra).</span><span class="sxs-lookup"><span data-stu-id="1cc0f-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1cc0f-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1cc0f-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cc0f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cc0f-112">Requirements</span></span>  
 <span data-ttu-id="1cc0f-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cc0f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cc0f-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1cc0f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1cc0f-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cc0f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cc0f-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cc0f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc0f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cc0f-117">See also</span></span>

- [<span data-ttu-id="1cc0f-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="1cc0f-118">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="1cc0f-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="1cc0f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
