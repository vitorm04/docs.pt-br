---
title: Método ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 628f85f3045533ead7ace47b11573a0b1a46df46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782043"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="cc18c-102">Método ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="cc18c-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="cc18c-103">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="cc18c-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc18c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc18c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc18c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cc18c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cc18c-106">no O número de caracteres no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="cc18c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cc18c-107">fora Um ponteiro para o número de caracteres realmente gravados no buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="cc18c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cc18c-108">fora Uma matriz de caracteres que contém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="cc18c-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc18c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc18c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cc18c-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cc18c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc18c-111">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="cc18c-111">Requirements</span></span>  
 <span data-ttu-id="cc18c-112">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc18c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc18c-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc18c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc18c-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc18c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc18c-115">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc18c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc18c-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="cc18c-116">See also</span></span>

- [<span data-ttu-id="cc18c-117">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="cc18c-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="cc18c-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="cc18c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
