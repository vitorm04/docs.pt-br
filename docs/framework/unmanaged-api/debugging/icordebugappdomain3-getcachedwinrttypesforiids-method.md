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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95c84f7f40db0096b26ec448f8f229cdbfe3afb1
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025899"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="17508-102">Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="17508-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="17508-103">Obtém um enumerador para os tipos de tempo de execução do Windows em cache em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="17508-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17508-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17508-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17508-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17508-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="17508-106">[in] O número de tipos necessários.</span><span class="sxs-lookup"><span data-stu-id="17508-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="17508-107">[in] Um ponteiro para uma matriz que contém os identificadores de interface correspondente para as representações gerenciadas dos tipos de tempo de execução do Windows a ser recuperado.</span><span class="sxs-lookup"><span data-stu-id="17508-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="17508-108">[out] Um ponteiro para o endereço de um objeto de interface de "ICorDebugTypeEnum" que permite a enumeração das representações gerenciadas em cache dos tipos de tempo de execução do Windows recuperados com base em identificadores de interface `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="17508-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17508-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="17508-109">Remarks</span></span>  
 <span data-ttu-id="17508-110">Se o método falha ao recuperar informações para um identificador de interface específica, a entrada correspondente na coleção "ICorDebugTypeEnum" terão um tipo de `ELEMENT_TYPE_END` erros devido a problemas de recuperação de dados, ou `ELEMENT_TYPE_VOID` para interface desconhecida identificadores.</span><span class="sxs-lookup"><span data-stu-id="17508-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17508-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17508-111">Requirements</span></span>  
 <span data-ttu-id="17508-112">**Plataformas:** Tempo de Execução do Windows</span><span class="sxs-lookup"><span data-stu-id="17508-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="17508-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17508-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17508-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17508-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17508-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17508-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17508-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17508-116">See also</span></span>

- [<span data-ttu-id="17508-117">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="17508-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
