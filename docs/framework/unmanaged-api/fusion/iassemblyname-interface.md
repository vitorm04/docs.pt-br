---
title: Interface IAssemblyName
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796558"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="33eec-102">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="33eec-102">IAssemblyName Interface</span></span>
<span data-ttu-id="33eec-103">Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.</span><span class="sxs-lookup"><span data-stu-id="33eec-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33eec-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="33eec-104">Methods</span></span>  
  
|<span data-ttu-id="33eec-105">Método</span><span class="sxs-lookup"><span data-stu-id="33eec-105">Method</span></span>|<span data-ttu-id="33eec-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="33eec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33eec-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="33eec-107">Clone Method</span></span>](iassemblyname-clone-method.md)|<span data-ttu-id="33eec-108">Cria uma cópia superficial desse `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="33eec-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="33eec-109">Método Finalize</span><span class="sxs-lookup"><span data-stu-id="33eec-109">Finalize Method</span></span>](iassemblyname-finalize-method.md)|<span data-ttu-id="33eec-110">Permite que `IAssemblyName` este objeto libere recursos e execute outras operações de limpeza antes que seu destruidor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="33eec-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="33eec-111">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="33eec-111">GetDisplayName Method</span></span>](iassemblyname-getdisplayname-method.md)|<span data-ttu-id="33eec-112">Obtém o nome legível do assembly referenciado por este `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="33eec-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="33eec-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="33eec-113">GetName Method</span></span>](iassemblyname-getname-method.md)|<span data-ttu-id="33eec-114">Obtém o nome simples e não criptografado do assembly referenciado por `IAssemblyName` esse objeto.</span><span class="sxs-lookup"><span data-stu-id="33eec-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="33eec-115">Método GetProperty</span><span class="sxs-lookup"><span data-stu-id="33eec-115">GetProperty Method</span></span>](iassemblyname-getproperty-method.md)|<span data-ttu-id="33eec-116">Obtém um ponteiro para a propriedade referenciada pelo especificado `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="33eec-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="33eec-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="33eec-117">GetVersion Method</span></span>](iassemblyname-getversion-method.md)|<span data-ttu-id="33eec-118">Obtém as informações de versão do assembly referenciado por `IAssemblyName` este objeto.</span><span class="sxs-lookup"><span data-stu-id="33eec-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="33eec-119">Método IsEqual</span><span class="sxs-lookup"><span data-stu-id="33eec-119">IsEqual Method</span></span>](iassemblyname-isequal-method.md)|<span data-ttu-id="33eec-120">Determina se um objeto `IAssemblyName` especificado é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificados.</span><span class="sxs-lookup"><span data-stu-id="33eec-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="33eec-121">Método SetProperty</span><span class="sxs-lookup"><span data-stu-id="33eec-121">SetProperty Method</span></span>](iassemblyname-setproperty-method.md)|<span data-ttu-id="33eec-122">Define o valor da propriedade referenciada pelo especificado `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="33eec-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33eec-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="33eec-123">Requirements</span></span>  
 <span data-ttu-id="33eec-124">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33eec-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33eec-125">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="33eec-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="33eec-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33eec-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33eec-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33eec-127">See also</span></span>

- [<span data-ttu-id="33eec-128">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="33eec-128">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="33eec-129">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="33eec-129">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
