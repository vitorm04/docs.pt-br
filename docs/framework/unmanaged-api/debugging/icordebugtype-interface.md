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
ms.openlocfilehash: 8210e67f4bdd615ff65d9bd3474043fc45fd8883
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791254"
---
# <a name="icordebugtype-interface"></a><span data-ttu-id="7f889-102">Interface ICorDebugType</span><span class="sxs-lookup"><span data-stu-id="7f889-102">ICorDebugType Interface</span></span>
<span data-ttu-id="7f889-103">Representa um tipo, básico ou complexo (ou seja, definido pelo usuário).</span><span class="sxs-lookup"><span data-stu-id="7f889-103">Represents a type, either basic or complex (that is, user-defined).</span></span> <span data-ttu-id="7f889-104">Se o tipo for genérico, `ICorDebugType` representará o tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="7f889-104">If the type is generic, `ICorDebugType` represents the instantiated generic type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f889-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7f889-105">Methods</span></span>  
  
|<span data-ttu-id="7f889-106">Método</span><span class="sxs-lookup"><span data-stu-id="7f889-106">Method</span></span>|<span data-ttu-id="7f889-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f889-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7f889-108">Método EnumerateTypeParameters</span><span class="sxs-lookup"><span data-stu-id="7f889-108">EnumerateTypeParameters Method</span></span>](icordebugtype-enumeratetypeparameters-method.md)|<span data-ttu-id="7f889-109">Obtém um ponteiro de interface para um ICorDebugTypeEnum que faz referência aos parâmetros de <xref:System.Type> genéricos da classe referenciada por este `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7f889-109">Gets an interface pointer to an ICorDebugTypeEnum that references the generic <xref:System.Type> parameters of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7f889-110">Método GetBase</span><span class="sxs-lookup"><span data-stu-id="7f889-110">GetBase Method</span></span>](icordebugtype-getbase-method.md)|<span data-ttu-id="7f889-111">Obtém um ponteiro de interface para um `ICorDebugType` que faz referência à classe base da classe referenciada por essa `ICorDebugType`, se existir uma.</span><span class="sxs-lookup"><span data-stu-id="7f889-111">Gets an interface pointer to an `ICorDebugType` that references the base class of the class referenced by this `ICorDebugType`, if one exists.</span></span>|  
|[<span data-ttu-id="7f889-112">Método GetClass</span><span class="sxs-lookup"><span data-stu-id="7f889-112">GetClass Method</span></span>](icordebugtype-getclass-method.md)|<span data-ttu-id="7f889-113">Obtém um ponteiro de interface para um ICorDebugClass que faz referência ao Construtor tipado dessa `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7f889-113">Gets an interface pointer to an ICorDebugClass that references the typed constructor of this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7f889-114">Método GetFirstTypeParameter</span><span class="sxs-lookup"><span data-stu-id="7f889-114">GetFirstTypeParameter Method</span></span>](icordebugtype-getfirsttypeparameter-method.md)|<span data-ttu-id="7f889-115">Obtém um ponteiro de interface para um `ICorDebugType` que faz referência ao primeiro parâmetro de <xref:System.Type> genérico para o construtor da classe referenciada por essa `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7f889-115">Gets an interface pointer to an `ICorDebugType` that references the first generic <xref:System.Type> parameter for the constructor of the class referenced by this `ICorDebugType`.</span></span>|  
|[<span data-ttu-id="7f889-116">Método GetRank</span><span class="sxs-lookup"><span data-stu-id="7f889-116">GetRank Method</span></span>](icordebugtype-getrank-method.md)|<span data-ttu-id="7f889-117">Obtém o número de dimensões em um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="7f889-117">Gets the number of dimensions in an array type.</span></span>|  
|[<span data-ttu-id="7f889-118">Método GetStaticFieldValue</span><span class="sxs-lookup"><span data-stu-id="7f889-118">GetStaticFieldValue Method</span></span>](icordebugtype-getstaticfieldvalue-method.md)|<span data-ttu-id="7f889-119">Obtém um ponteiro de interface para um ICorDebugValue que contém o valor do campo estático referenciado pelo token de campo especificado no quadro de ativação especificado.</span><span class="sxs-lookup"><span data-stu-id="7f889-119">Gets an interface pointer to an ICorDebugValue that contains the value of the static field referenced by the specified field token in the specified stack frame.</span></span>|  
|[<span data-ttu-id="7f889-120">Método GetType</span><span class="sxs-lookup"><span data-stu-id="7f889-120">GetType Method</span></span>](icordebugtype-gettype-method.md)|<span data-ttu-id="7f889-121">Obtém um valor de CorElementType que descreve o tipo nativo do Common Language Runtime <xref:System.Type> referenciado por esse `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7f889-121">Gets a CorElementType value that describes the native type of the common language runtime <xref:System.Type> referenced by this `ICorDebugType`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f889-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f889-122">Remarks</span></span>  
 <span data-ttu-id="7f889-123">Se o tipo for genérico, `ICorDebugClass` representará o tipo não instanciado.</span><span class="sxs-lookup"><span data-stu-id="7f889-123">If the type is generic, `ICorDebugClass` represents the uninstantiated type.</span></span> <span data-ttu-id="7f889-124">A interface `ICorDebugType` representa um tipo genérico instanciado.</span><span class="sxs-lookup"><span data-stu-id="7f889-124">The `ICorDebugType` interface represents an instantiated generic type.</span></span> <span data-ttu-id="7f889-125">Por exemplo, a tabela de hash\<K, V > seria representada por `ICorDebugClass`, enquanto a Hashtable\<Int32, a cadeia de caracteres > seria representada por `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7f889-125">For example, Hashtable\<K, V> would be represented by `ICorDebugClass`, whereas Hashtable\<Int32, String> would be represented by `ICorDebugType`.</span></span>  
  
 <span data-ttu-id="7f889-126">Tipos não genéricos são representados por `ICorDebugClass` e `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="7f889-126">Non-generic types are represented by both `ICorDebugClass` and `ICorDebugType`.</span></span> <span data-ttu-id="7f889-127">A última interface foi introduzida no .NET Framework versão 2,0 para lidar com a instanciação de tipo.</span><span class="sxs-lookup"><span data-stu-id="7f889-127">The latter interface was introduced in the .NET Framework version 2.0 to deal with type instantiation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f889-128">Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.</span><span class="sxs-lookup"><span data-stu-id="7f889-128">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f889-129">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7f889-129">Requirements</span></span>  
 <span data-ttu-id="7f889-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f889-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f889-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f889-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f889-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f889-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f889-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f889-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f889-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="7f889-134">See also</span></span>

- [<span data-ttu-id="7f889-135">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="7f889-135">Debugging Interfaces</span></span>](debugging-interfaces.md)
