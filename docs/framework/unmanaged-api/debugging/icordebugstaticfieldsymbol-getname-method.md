---
title: 'Método ICorDebugStaticFieldSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 75f5324296f9b42406157d06351f7e680a749444
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378743"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="d82b4-102">Método ICorDebugStaticFieldSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="d82b4-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="d82b4-103">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="d82b4-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d82b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d82b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d82b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d82b4-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d82b4-106">no O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="d82b4-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d82b4-107">fora Um ponteiro para o número de caracteres realmente gravados no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="d82b4-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="d82b4-108">fora Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="d82b4-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d82b4-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="d82b4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d82b4-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d82b4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d82b4-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d82b4-111">Requirements</span></span>  
 <span data-ttu-id="d82b4-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d82b4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d82b4-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d82b4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d82b4-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d82b4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d82b4-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d82b4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d82b4-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d82b4-116">See also</span></span>

- [<span data-ttu-id="d82b4-117">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="d82b4-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="d82b4-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d82b4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
