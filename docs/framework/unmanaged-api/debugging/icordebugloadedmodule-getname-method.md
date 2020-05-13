---
title: Método ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4a0c4e99f23dc949b0bbaa8bbda35cff1537cf3c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209858"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="b7ec3-102">Método ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="b7ec3-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="b7ec3-103">Obtém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="b7ec3-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7ec3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7ec3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7ec3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7ec3-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b7ec3-106">no O número de caracteres no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="b7ec3-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b7ec3-107">fora Um ponteiro para o número de caracteres realmente gravados no `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="b7ec3-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b7ec3-108">fora Uma matriz de caracteres que contém o nome do módulo carregado.</span><span class="sxs-lookup"><span data-stu-id="b7ec3-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7ec3-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7ec3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b7ec3-110">Esse método está disponível somente com .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b7ec3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7ec3-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7ec3-111">Requirements</span></span>  
 <span data-ttu-id="b7ec3-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7ec3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7ec3-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7ec3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7ec3-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7ec3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7ec3-115">**.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7ec3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7ec3-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="b7ec3-116">See also</span></span>

- [<span data-ttu-id="b7ec3-117">Interface ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="b7ec3-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="b7ec3-118">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="b7ec3-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
