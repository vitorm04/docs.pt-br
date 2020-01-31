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
ms.openlocfilehash: 6f9bcec66ff613d19c1198ac9849ca28c978f537
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788939"
---
# <a name="icordebugappdomain2-interface"></a><span data-ttu-id="950b2-102">Interface ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="950b2-102">ICorDebugAppDomain2 Interface</span></span>

<span data-ttu-id="950b2-103">Fornece métodos para trabalhar com matrizes, ponteiros, ponteiros de função e tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="950b2-103">Provides methods to work with arrays, pointers, function pointers, and reference types.</span></span> <span data-ttu-id="950b2-104">Essa interface é uma extensão da interface ICorDebugAppDomain.</span><span class="sxs-lookup"><span data-stu-id="950b2-104">This interface is an extension of the ICorDebugAppDomain interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="950b2-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="950b2-105">Methods</span></span>  
  
|<span data-ttu-id="950b2-106">Método</span><span class="sxs-lookup"><span data-stu-id="950b2-106">Method</span></span>|<span data-ttu-id="950b2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="950b2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="950b2-108">Método GetArrayOrPointerType</span><span class="sxs-lookup"><span data-stu-id="950b2-108">GetArrayOrPointerType Method</span></span>](icordebugappdomain2-getarrayorpointertype-method.md)|<span data-ttu-id="950b2-109">Obtém uma matriz do tipo especificado ou um ponteiro ou uma referência para o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="950b2-109">Gets an array of the specified type, or a pointer or reference to the specified type.</span></span>|  
|[<span data-ttu-id="950b2-110">GetFunctionPointerType</span><span class="sxs-lookup"><span data-stu-id="950b2-110">GetFunctionPointerType</span></span>](icordebugappdomain2-getfunctionpointertype-method.md)|<span data-ttu-id="950b2-111">Obtém um ponteiro para uma função que tem uma determinada assinatura.</span><span class="sxs-lookup"><span data-stu-id="950b2-111">Gets a pointer to a function that has a given signature.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="950b2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="950b2-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="950b2-113">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="950b2-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="950b2-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="950b2-114">Requirements</span></span>  
 <span data-ttu-id="950b2-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="950b2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="950b2-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="950b2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="950b2-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="950b2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="950b2-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="950b2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="950b2-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="950b2-119">See also</span></span>

- [<span data-ttu-id="950b2-120">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="950b2-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
