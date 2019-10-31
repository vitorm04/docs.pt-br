---
title: Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypesForIIDs
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs method, [.NET Framework debugging]
- GetCachedWinRTTypesForIIDs method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 23682ca0-1bcf-48e6-996e-69f7ba337682
topic_type:
- apiref
ms.openlocfilehash: 0369cc6d98736542b764e5914d733a9341753b24
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088873"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="f65a6-102">Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="f65a6-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="f65a6-103">Obtém um enumerador para tipos de Windows Runtime em cache em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="f65a6-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f65a6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f65a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f65a6-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="f65a6-106">no O número de tipos necessários.</span><span class="sxs-lookup"><span data-stu-id="f65a6-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="f65a6-107">no Um ponteiro para uma matriz que contém os identificadores de interface correspondentes às representações gerenciadas dos tipos de Windows Runtime a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="f65a6-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="f65a6-108">fora Um ponteiro para o endereço de um objeto de interface "ICorDebugTypeEnum" que permite a enumeração das representações gerenciadas em cache dos tipos de Windows Runtime recuperados, com base nos identificadores de interface no `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="f65a6-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f65a6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f65a6-109">Remarks</span></span>  
 <span data-ttu-id="f65a6-110">Se o método não conseguir recuperar informações para um identificador de interface específico, a entrada correspondente na coleção "ICorDebugTypeEnum" terá um tipo de `ELEMENT_TYPE_END` para erros devido a problemas de recuperação de dados ou `ELEMENT_TYPE_VOID` para identificadores de interface desconhecidos.</span><span class="sxs-lookup"><span data-stu-id="f65a6-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f65a6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f65a6-111">Requirements</span></span>  
 <span data-ttu-id="f65a6-112">**Plataformas:** Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="f65a6-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="f65a6-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f65a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f65a6-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f65a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f65a6-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f65a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f65a6-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f65a6-116">See also</span></span>

- [<span data-ttu-id="f65a6-117">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="f65a6-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
