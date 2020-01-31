---
title: 'Método ICorDebugStaticFieldSymbol:: GetName'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 0e4c52ff1ae6113ee2c3990a9d91682e10141902
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791826"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="826e1-102">Método ICorDebugStaticFieldSymbol:: GetName</span><span class="sxs-lookup"><span data-stu-id="826e1-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="826e1-103">Obtém o nome do campo estático.</span><span class="sxs-lookup"><span data-stu-id="826e1-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826e1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="826e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="826e1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="826e1-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="826e1-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="826e1-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="826e1-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="826e1-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="826e1-108">fora Uma matriz de caracteres que armazena o nome retornado.</span><span class="sxs-lookup"><span data-stu-id="826e1-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="826e1-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="826e1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="826e1-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="826e1-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826e1-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="826e1-111">Requirements</span></span>  
 <span data-ttu-id="826e1-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="826e1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826e1-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="826e1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="826e1-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="826e1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="826e1-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="826e1-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826e1-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="826e1-116">See also</span></span>

- [<span data-ttu-id="826e1-117">Interface ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="826e1-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="826e1-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="826e1-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
