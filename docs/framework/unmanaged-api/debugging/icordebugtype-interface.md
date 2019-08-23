---
title: Interface ICorDebugType
ms.date: 03/30/2017
api_name:
- ICorDebugType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType
helpviewer_keywords:
- ICorDebugType interface [.NET Framework debugging]
ms.assetid: 94e02e31-67ea-4b00-8148-a46740a4571d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b830af5d59c0eb177d815451ecedbdc14121aaad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964754"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="4f0c8-102">Interface ICorDebugType</span><span class="sxs-lookup"><span data-stu-id="4f0c8-102">ICorDebugType Interface</span></span>
<span data-ttu-id="4f0c8-103">Representa um tipo, básico ou complexo (ou seja, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="4f0c8-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="4f0c8-104">Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4f0c8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4f0c8-105">Methods</span></span>  
  
|<span data-ttu-id="4f0c8-106">Método</span><span class="sxs-lookup"><span data-stu-id="4f0c8-106">Method</span></span>|<span data-ttu-id="4f0c8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4f0c8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4f0c8-108">Método EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="4f0c8-108">EnumerateTypeParameters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="4f0c8-109">Obtém um ponteiro de interface para um ICorDebugTypeEnum que faz referência <xref:System.Type> aos parâmetros genéricos da classe referenciada `ICorDebugType`por isso.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="4f0c8-110">Método GetBase</span><span class="sxs-lookup"><span data-stu-id="4f0c8-110">GetBase Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getbase-method.md)|<span data-ttu-id="4f0c8-111">Obtém um ponteiro de interface para `ICorDebugType` um que faz referência à classe base da classe referenciada `ICorDebugType`por isso, se houver.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="4f0c8-112">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="4f0c8-112">GetClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)|<span data-ttu-id="4f0c8-113">Obtém um ponteiro de interface para um ICorDebugClass que faz referência ao Construtor tipado deste `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="4f0c8-114">Método GetFirstTypeParameter</span><span class="sxs-lookup"><span data-stu-id="4f0c8-114">GetFirstTypeParameter Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="4f0c8-115">Obtém um ponteiro de interface para `ICorDebugType` um que faz referência ao <xref:System.Type> primeiro parâmetro genérico para o construtor da classe referenciada `ICorDebugType`por isso.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="4f0c8-116">Método GetRank</span><span class="sxs-lookup"><span data-stu-id="4f0c8-116">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getrank-method.md)|<span data-ttu-id="4f0c8-117">Obtém o número de dimensões em um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="4f0c8-118">Método GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="4f0c8-118">GetStaticFieldValue Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="4f0c8-119">Obtém um ponteiro de interface para um ICorDebugValue que contém o valor do campo estático referenciado pelo token de campo especificado no quadro de ativação especificado.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="4f0c8-120">Método GetType</span><span class="sxs-lookup"><span data-stu-id="4f0c8-120">GetType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)|<span data-ttu-id="4f0c8-121">Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime <xref:System.Type> referenciado por `ICorDebugType`isso.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4f0c8-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f0c8-122">Remarks</span></span>  
 <span data-ttu-id="4f0c8-123">Se o tipo for genérico, `ICorDebugClass` representará o tipo não instanciado.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="4f0c8-124">A `ICorDebugType` interface representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="4f0c8-125">Por exemplo, a\<tabela de hash K, V > seria `ICorDebugClass`representada por,\<enquanto a Hashtable Int32, a cadeia de `ICorDebugType`caracteres > seria representada por.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="4f0c8-126">Tipos não genéricos são representados por `ICorDebugClass` e. `ICorDebugType`</span><span class="sxs-lookup"><span data-stu-id="4f0c8-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="4f0c8-127">A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f0c8-128">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="4f0c8-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f0c8-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4f0c8-129">Requirements</span></span>  
 <span data-ttu-id="4f0c8-130">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f0c8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f0c8-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4f0c8-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4f0c8-132">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4f0c8-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f0c8-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f0c8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0c8-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f0c8-134">See also</span></span>

- [<span data-ttu-id="4f0c8-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4f0c8-135">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
