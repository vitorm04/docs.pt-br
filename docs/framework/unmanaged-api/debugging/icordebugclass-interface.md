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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ad830e728fbe764085a5808a48e4cacedc595
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133621"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="e3442-102">Interface ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="e3442-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="e3442-103">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="e3442-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="e3442-104">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="e3442-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e3442-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="e3442-105">Methods</span></span>  
  
|<span data-ttu-id="e3442-106">Método</span><span class="sxs-lookup"><span data-stu-id="e3442-106">Method</span></span>|<span data-ttu-id="e3442-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e3442-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e3442-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="e3442-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="e3442-109">Obtém o módulo que define essa classe.</span><span class="sxs-lookup"><span data-stu-id="e3442-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="e3442-110">Método GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="e3442-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="e3442-111">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="e3442-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="e3442-112">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="e3442-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="e3442-113">Obtém o `TypeDef` token de metadados para essa classe.</span><span class="sxs-lookup"><span data-stu-id="e3442-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e3442-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3442-114">Remarks</span></span>  
 <span data-ttu-id="e3442-115">O `ICorDebugClass` interface representa um tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="e3442-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="e3442-116">A interface ICorDebugType representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="e3442-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="e3442-117">Por exemplo, `Hashtable<K, V>` seria representada por `ICorDebugClass`, enquanto `Hashtable<Int32, String>` seria representada pelo `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e3442-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="e3442-118">Tipos não genéricos são representados por ambos `ICorDebugClass` e `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="e3442-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="e3442-119">A segunda interface foi introduzida no .NET Framework versão 2.0 para lidar com uma instância de tipo.</span><span class="sxs-lookup"><span data-stu-id="e3442-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3442-120">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="e3442-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3442-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e3442-121">Requirements</span></span>  
 <span data-ttu-id="e3442-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3442-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3442-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e3442-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e3442-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3442-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e3442-125">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e3442-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3442-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3442-126">See also</span></span>

- [<span data-ttu-id="e3442-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="e3442-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
