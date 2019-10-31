---
title: Interface ICorDebugClass
ms.date: 03/30/2017
api_name:
- ICorDebugClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass
helpviewer_keywords:
- ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type:
- apiref
ms.openlocfilehash: 5714597b5e5ca2936aad53217ae934684e75585c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125745"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="a1fb8-102">Interface ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="a1fb8-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="a1fb8-103">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="a1fb8-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="a1fb8-104">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1fb8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a1fb8-105">Methods</span></span>  
  
|<span data-ttu-id="a1fb8-106">Método</span><span class="sxs-lookup"><span data-stu-id="a1fb8-106">Method</span></span>|<span data-ttu-id="a1fb8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1fb8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1fb8-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="a1fb8-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="a1fb8-109">Obtém o módulo que define essa classe.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="a1fb8-110">Método GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="a1fb8-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="a1fb8-111">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="a1fb8-112">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="a1fb8-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="a1fb8-113">Obtém o token de metadados `TypeDef` para esta classe.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1fb8-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1fb8-114">Remarks</span></span>  
 <span data-ttu-id="a1fb8-115">A interface `ICorDebugClass` representa um tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="a1fb8-116">A interface ICorDebugType representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="a1fb8-117">Por exemplo, `Hashtable<K, V>` seria representado por `ICorDebugClass`, enquanto `Hashtable<Int32, String>` seria representado por `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="a1fb8-118">Tipos não genéricos são representados por `ICorDebugClass` e `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="a1fb8-119">A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1fb8-120">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="a1fb8-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1fb8-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1fb8-121">Requirements</span></span>  
 <span data-ttu-id="a1fb8-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1fb8-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1fb8-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1fb8-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1fb8-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1fb8-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1fb8-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1fb8-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1fb8-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1fb8-126">See also</span></span>

- [<span data-ttu-id="a1fb8-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="a1fb8-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
