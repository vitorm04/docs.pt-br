---
title: ICorDebugAppDomain2 Interface1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4549b0fe6379979a7b9bd6344d65ff465f33f17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506128"
---
# <a name="icordebugappdomain2-interface1"></a><span data-ttu-id="aeb05-102">ICorDebugAppDomain2 Interface1</span><span class="sxs-lookup"><span data-stu-id="aeb05-102">ICorDebugAppDomain2 Interface1</span></span>
<span data-ttu-id="aeb05-103">Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="aeb05-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="aeb05-104">Essa interface é uma extensão da interface ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="aeb05-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aeb05-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="aeb05-105">Methods</span></span>  
  
|<span data-ttu-id="aeb05-106">Método</span><span class="sxs-lookup"><span data-stu-id="aeb05-106">Method</span></span>|<span data-ttu-id="aeb05-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="aeb05-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aeb05-108">Método GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="aeb05-108">GetArrayOrPointerType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="aeb05-109">Obtém uma matriz do tipo especificado, ou um ponteiro ou referência ao tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="aeb05-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="aeb05-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="aeb05-110">GetFunctionPointerType</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="aeb05-111">Obtém um ponteiro para uma função que tem uma determinada assinatura.</span><span class="sxs-lookup"><span data-stu-id="aeb05-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb05-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="aeb05-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aeb05-113">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="aeb05-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aeb05-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aeb05-114">Requirements</span></span>  
 <span data-ttu-id="aeb05-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aeb05-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aeb05-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aeb05-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aeb05-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aeb05-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aeb05-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aeb05-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeb05-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aeb05-119">See also</span></span>
- [<span data-ttu-id="aeb05-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="aeb05-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
