---
title: Interface ICorDebugAppDomain2
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain2
helpviewer_keywords:
- ICorDebugAppDomain2 interface [.NET Framework debugging]
ms.assetid: 314d29f3-feb0-4a92-9530-b569c280cc31
topic_type:
- apiref
ms.openlocfilehash: 1643d91f373ff233540026440ee21aa4c146f3e3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895129"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="c365b-102">Interface ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="c365b-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="c365b-103">Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="c365b-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="c365b-104">Essa interface é uma extensão da interface ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="c365b-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c365b-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="c365b-105">Methods</span></span>  
  
|<span data-ttu-id="c365b-106">Método</span><span class="sxs-lookup"><span data-stu-id="c365b-106">Method</span></span>|<span data-ttu-id="c365b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c365b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c365b-108">Método GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="c365b-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="c365b-109">Obtém uma matriz do tipo especificado ou um ponteiro ou uma referência para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="c365b-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="c365b-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="c365b-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="c365b-111">Obtém um ponteiro para uma função que tem uma determinada assinatura.</span><span class="sxs-lookup"><span data-stu-id="c365b-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c365b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="c365b-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c365b-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="c365b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c365b-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c365b-114">Requirements</span></span>  
 <span data-ttu-id="c365b-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c365b-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c365b-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c365b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c365b-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c365b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c365b-118">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c365b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c365b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c365b-119">See also</span></span>

- [<span data-ttu-id="c365b-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="c365b-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
