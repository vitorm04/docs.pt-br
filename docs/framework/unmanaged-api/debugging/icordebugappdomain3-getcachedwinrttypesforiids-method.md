---
title: "Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5a7ce44dcfc709b4fea1952471cf31f5f07d4d0e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="9ef96-102">Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="9ef96-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="9ef96-103">Obtém um enumerador para armazenada em cache [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="9ef96-103">Gets an enumerator for cached [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ef96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ef96-104">Syntax</span></span>  
  
```  
HRESULT GetCachedWinRTTypesForIIDs (   
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ef96-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ef96-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="9ef96-106">[in] O número de tipos necessários.</span><span class="sxs-lookup"><span data-stu-id="9ef96-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="9ef96-107">[in] Um ponteiro para uma matriz que contém os identificadores de interface correspondente para as representações gerenciadas do [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="9ef96-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="9ef96-108">[out] Um ponteiro para o endereço de um objeto de interface de "ICorDebugTypeEnum" que permite a enumeração de cache gerenciado representações do [!INCLUDE[wrt](../../../../includes/wrt-md.md)] tipos recuperados com base em identificadores de interface `iidsToResolve`.</span><span class="sxs-lookup"><span data-stu-id="9ef96-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the [!INCLUDE[wrt](../../../../includes/wrt-md.md)] types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ef96-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ef96-109">Remarks</span></span>  
 <span data-ttu-id="9ef96-110">Se o método falhar recuperar informações de um identificador de interface específica, a entrada correspondente na coleção "ICorDebugTypeEnum" terá um tipo de `ELEMENT_TYPE_END` erros devido a problemas de recuperação de dados, ou `ELEMENT_TYPE_VOID` para interface desconhecida identificadores.</span><span class="sxs-lookup"><span data-stu-id="9ef96-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ef96-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ef96-111">Requirements</span></span>  
 <span data-ttu-id="9ef96-112">**Plataformas:**[!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef96-112">**Platforms:** [!INCLUDE[wrt](../../../../includes/wrt-md.md)]</span></span>  
  
 <span data-ttu-id="9ef96-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ef96-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ef96-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ef96-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ef96-115">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ef96-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ef96-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ef96-116">See Also</span></span>  
 [<span data-ttu-id="9ef96-117">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="9ef96-117">ICorDebugAppDomain3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
