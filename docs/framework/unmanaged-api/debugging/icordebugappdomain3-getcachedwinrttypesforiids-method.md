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
ms.openlocfilehash: f8e92ec4f813e8810273a1514298d0739a3d2406
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179056"
---
# <a name="icordebugappdomain3getcachedwinrttypesforiids-method"></a><span data-ttu-id="6fcd8-102">Método ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs</span><span class="sxs-lookup"><span data-stu-id="6fcd8-102">ICorDebugAppDomain3::GetCachedWinRTTypesForIIDs Method</span></span>
<span data-ttu-id="6fcd8-103">Obtém um enumerador para tipos de tempo de execução do Windows em cache em um domínio de aplicativo com base em seus identificadores de interface.</span><span class="sxs-lookup"><span data-stu-id="6fcd8-103">Gets an enumerator for cached Windows Runtime types in an application domain based on their interface identifiers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fcd8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fcd8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedWinRTTypesForIIDs (
    [in]  ULONG32            cReqTypes,  
    [in]  GUID                *iidsToResolve,  
    [out] ICorDebugTypeEnum   **ppTypesEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fcd8-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fcd8-105">Parameters</span></span>  
 `cReqTypes`  
 <span data-ttu-id="6fcd8-106">[em] O número de tipos necessários.</span><span class="sxs-lookup"><span data-stu-id="6fcd8-106">[in] The number of required types.</span></span>  
  
 `iidsToResolve`  
 <span data-ttu-id="6fcd8-107">[em] Um ponteiro para uma matriz que contém os identificadores de interface correspondentes às representações gerenciadas dos tipos de tempo de execução do Windows a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="6fcd8-107">[in] A pointer to an array that contains the interface identifiers corresponding to the managed representations of the Windows Runtime types to be retrieved.</span></span>  
  
 `ppTypesEnum`  
 <span data-ttu-id="6fcd8-108">[fora] Um ponteiro para o endereço de um objeto de interface "ICorDebugTypeEnum" que permite a enumeração das representações gerenciadas `iidsToResolve`em cache dos tipos de tempo de execução do Windows recuperados, com base nos identificadores de interface em .</span><span class="sxs-lookup"><span data-stu-id="6fcd8-108">[out] A pointer to the address of an "ICorDebugTypeEnum" interface object that allows enumeration of the cached managed representations of the Windows Runtime types retrieved, based on the interface identifiers in `iidsToResolve`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6fcd8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fcd8-109">Remarks</span></span>  
 <span data-ttu-id="6fcd8-110">Se o método não recuperar informações para um identificador de interface específico, a entrada correspondente na `ELEMENT_TYPE_END` coleção "ICorDebugTypeEnum" `ELEMENT_TYPE_VOID` terá um tipo de erros devido a problemas de recuperação de dados ou para identificadores de interface desconhecidos.</span><span class="sxs-lookup"><span data-stu-id="6fcd8-110">If the method fails to retrieve information for a specific interface identifier, the corresponding entry in the "ICorDebugTypeEnum" collection will have a type of `ELEMENT_TYPE_END` for errors due to data retrieval issues, or `ELEMENT_TYPE_VOID` for unknown interface identifiers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fcd8-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6fcd8-111">Requirements</span></span>  
 <span data-ttu-id="6fcd8-112">**Plataformas:** Tempo de execução do Windows</span><span class="sxs-lookup"><span data-stu-id="6fcd8-112">**Platforms:** Windows Runtime</span></span>  
  
 <span data-ttu-id="6fcd8-113">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6fcd8-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fcd8-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6fcd8-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fcd8-115">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fcd8-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fcd8-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="6fcd8-116">See also</span></span>

- [<span data-ttu-id="6fcd8-117">Interface ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="6fcd8-117">ICorDebugAppDomain3 Interface</span></span>](icordebugappdomain3-interface.md)
