---
title: ICorDebugClass Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugClass
helpviewer_keywords: ICorDebugClass interface [.NET Framework debugging]
ms.assetid: 03a6facb-f12f-49be-9839-e73b9c791cd5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79e93a44f2cc532286a7e9b01fa32292a4e1c69a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugclass-interface1"></a><span data-ttu-id="14479-102">ICorDebugClass Interface1</span><span class="sxs-lookup"><span data-stu-id="14479-102">ICorDebugClass Interface1</span></span>
<span data-ttu-id="14479-103">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="14479-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="14479-104">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="14479-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="14479-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="14479-105">Methods</span></span>  
  
|<span data-ttu-id="14479-106">Método</span><span class="sxs-lookup"><span data-stu-id="14479-106">Method</span></span>|<span data-ttu-id="14479-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="14479-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="14479-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="14479-108">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|<span data-ttu-id="14479-109">Obtém o módulo que define essa classe.</span><span class="sxs-lookup"><span data-stu-id="14479-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="14479-110">Método GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="14479-110">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="14479-111">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="14479-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="14479-112">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="14479-112">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-gettoken-method.md)|<span data-ttu-id="14479-113">Obtém o `TypeDef` token de metadados para essa classe.</span><span class="sxs-lookup"><span data-stu-id="14479-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14479-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="14479-114">Remarks</span></span>  
 <span data-ttu-id="14479-115">O `ICorDebugClass` interface representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="14479-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="14479-116">A interface ICorDebugType representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="14479-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="14479-117">Por exemplo, `Hashtable<K, V>` poderia ser representado por `ICorDebugClass`, enquanto `Hashtable<Int32, String>` poderia ser representado por `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14479-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="14479-118">Tipos genéricos não são representados por ambos `ICorDebugClass` e `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="14479-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="14479-119">A segunda interface foi introduzida no .NET Framework versão 2.0 para lidar com uma instância de tipo.</span><span class="sxs-lookup"><span data-stu-id="14479-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14479-120">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="14479-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14479-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="14479-121">Requirements</span></span>  
 <span data-ttu-id="14479-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14479-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14479-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="14479-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="14479-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14479-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14479-125">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14479-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14479-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14479-126">See Also</span></span>  
 [<span data-ttu-id="14479-127">Interfaces de depuração</span><span class="sxs-lookup"><span data-stu-id="14479-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
