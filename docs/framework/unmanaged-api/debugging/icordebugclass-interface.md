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
ms.openlocfilehash: 7ac588591222a1abbc7b99ec7e973284c055f95e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784163"
---
# <a name="icordebugclass-interface"></a><span data-ttu-id="4c2fc-102">Interface ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="4c2fc-102">ICorDebugClass Interface</span></span>

<span data-ttu-id="4c2fc-103">Representa um tipo, que pode ser básico ou complexo (isto é, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="4c2fc-103">Represents a type, which can be either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="4c2fc-104">Se o tipo for genérico, `ICorDebugClass` representará o tipo genérico sem instância.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-104">If the type is generic, `ICorDebugClass` represents the uninstantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c2fc-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4c2fc-105">Methods</span></span>  
  
|<span data-ttu-id="4c2fc-106">Método</span><span class="sxs-lookup"><span data-stu-id="4c2fc-106">Method</span></span>|<span data-ttu-id="4c2fc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c2fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c2fc-108">Método GetModule</span><span class="sxs-lookup"><span data-stu-id="4c2fc-108">GetModule Method</span></span>](icordebugclass-getmodule-method.md)|<span data-ttu-id="4c2fc-109">Obtém o módulo que define essa classe.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-109">Gets the module that defines this class.</span></span>|  
|[<span data-ttu-id="4c2fc-110">Método GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="4c2fc-110">GetStaticFieldValue Method</span></span>](icordebugclass-getstaticfieldvalue-method.md)|<span data-ttu-id="4c2fc-111">Obtém o valor do campo estático especificado.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-111">Gets the value of the specified static field.</span></span>|  
|[<span data-ttu-id="4c2fc-112">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="4c2fc-112">GetToken Method</span></span>](icordebugclass-gettoken-method.md)|<span data-ttu-id="4c2fc-113">Obtém o token de metadados `TypeDef` para esta classe.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-113">Gets the `TypeDef` metadata token for this class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c2fc-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="4c2fc-114">Remarks</span></span>  
 <span data-ttu-id="4c2fc-115">A interface `ICorDebugClass` representa um tipo genérico não instanciado.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-115">The `ICorDebugClass` interface represents an uninstantiated generic type.</span></span> <span data-ttu-id="4c2fc-116">A interface ICorDebugType representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-116">The ICorDebugType interface represents an instantiated generic type.</span></span> <span data-ttu-id="4c2fc-117">Por exemplo, `Hashtable<K, V>` seria representado por `ICorDebugClass`, enquanto `Hashtable<Int32, String>` seria representado por `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-117">For example, `Hashtable<K, V>` would be represented by `ICorDebugClass`, whereas `Hashtable<Int32, String>` would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="4c2fc-118">Tipos não genéricos são representados por `ICorDebugClass` e `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-118">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="4c2fc-119">A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-119">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c2fc-120">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4c2fc-120">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c2fc-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="4c2fc-121">Requirements</span></span>  
 <span data-ttu-id="4c2fc-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c2fc-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c2fc-123">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4c2fc-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c2fc-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c2fc-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c2fc-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c2fc-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2fc-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="4c2fc-126">See also</span></span>

- [<span data-ttu-id="4c2fc-127">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4c2fc-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
