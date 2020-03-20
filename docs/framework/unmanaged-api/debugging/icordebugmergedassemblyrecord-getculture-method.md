---
title: ICorDebugMergeDRecord::Método GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: ad54a93b16e803170987dd56d8063669f7e67f94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178746"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="06b38-102">ICorDebugMergeDRecord::Método GetCulture</span><span class="sxs-lookup"><span data-stu-id="06b38-102">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>
<span data-ttu-id="06b38-103">Fica a seqüência de nomes de cultura da assembléia.</span><span class="sxs-lookup"><span data-stu-id="06b38-103">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b38-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06b38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b38-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="06b38-105">Parameters</span></span>  
 `cchCulture`  
 <span data-ttu-id="06b38-106">[em] O número de `szCulture` caracteres no buffer.</span><span class="sxs-lookup"><span data-stu-id="06b38-106">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="06b38-107">[fora] O número de caracteres `szCulture` realmente escritos para o buffer.</span><span class="sxs-lookup"><span data-stu-id="06b38-107">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="06b38-108">[fora] Uma matriz de caracteres que contém o nome da cultura.</span><span class="sxs-lookup"><span data-stu-id="06b38-108">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06b38-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="06b38-109">Remarks</span></span>  
 <span data-ttu-id="06b38-110">O nome da cultura é uma cadeia única que identifica uma cultura, como "en-US" (para a cultura inglesa (Estados Unidos) ou "neutra" (para uma cultura neutra).</span><span class="sxs-lookup"><span data-stu-id="06b38-110">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06b38-111">Este método está disponível apenas com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="06b38-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06b38-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="06b38-112">Requirements</span></span>  
 <span data-ttu-id="06b38-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06b38-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06b38-114">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06b38-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06b38-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06b38-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06b38-116">**.NET Framework Versions:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06b38-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b38-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="06b38-117">See also</span></span>

- [<span data-ttu-id="06b38-118">Interface ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="06b38-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="06b38-119">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="06b38-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
