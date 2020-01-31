---
title: 'Método ICorDebugMergedAssemblyRecord:: getculture'
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: 77ad8ee7977096e87b9fd2e131920a042243560e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793153"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="d473c-102">Método ICorDebugMergedAssemblyRecord:: getculture</span><span class="sxs-lookup"><span data-stu-id="d473c-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="d473c-103">Obtém a cadeia de caracteres do nome da cultura do assembly.</span><span class="sxs-lookup"><span data-stu-id="d473c-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d473c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d473c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,   
   [out] ULONG32 *pcchCulture,   
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d473c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d473c-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="d473c-106">no O número de caracteres no buffer de `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="d473c-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="d473c-107">fora O número de caracteres realmente gravados no buffer de `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="d473c-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="d473c-108">fora Uma matriz de caracteres que contém o nome da cultura.</span><span class="sxs-lookup"><span data-stu-id="d473c-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d473c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d473c-109">Remarks</span></span>  
 <span data-ttu-id="d473c-110">O nome da cultura é uma cadeia de caracteres exclusiva que identifica uma cultura, como "en-US" (para a cultura em inglês (Estados Unidos)) ou "neutro" (para uma cultura neutra).</span><span class="sxs-lookup"><span data-stu-id="d473c-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d473c-111">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d473c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d473c-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="d473c-112">Requirements</span></span>  
 <span data-ttu-id="d473c-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d473c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d473c-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d473c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d473c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d473c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d473c-116">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d473c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d473c-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="d473c-117">See also</span></span>

- [<span data-ttu-id="d473c-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="d473c-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d473c-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d473c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
