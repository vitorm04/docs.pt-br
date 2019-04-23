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
ms.openlocfilehash: 0d8d59ef282818dd9852d0ff8d2ec2abd40986d0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097129"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="c3f8f-102">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="c3f8f-102">IAssemblyName Interface</span></span>
<span data-ttu-id="c3f8f-103">Fornece métodos para descrever e trabalhar com a identidade exclusiva de um assembly.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3f8f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="c3f8f-104">Methods</span></span>  
  
|<span data-ttu-id="c3f8f-105">Método</span><span class="sxs-lookup"><span data-stu-id="c3f8f-105">Method</span></span>|<span data-ttu-id="c3f8f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3f8f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3f8f-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="c3f8f-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="c3f8f-108">Cria uma cópia superficial desse `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c3f8f-109">Método Finalize</span><span class="sxs-lookup"><span data-stu-id="c3f8f-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="c3f8f-110">Permite que isso `IAssemblyName` objeto para liberar recursos e executar outras operações de limpeza antes que seu destruidor é chamado.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="c3f8f-111">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="c3f8f-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="c3f8f-112">Obtém o nome legível do assembly referenciado por este `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c3f8f-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="c3f8f-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="c3f8f-114">Obtém o nome simple e não criptografado do assembly referenciado por este `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c3f8f-115">Método GetProperty</span><span class="sxs-lookup"><span data-stu-id="c3f8f-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="c3f8f-116">Obtém um ponteiro para a propriedade referenciada pelo especificado `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="c3f8f-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="c3f8f-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="c3f8f-118">Obtém as informações de versão do assembly referenciado por este `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="c3f8f-119">Método IsEqual</span><span class="sxs-lookup"><span data-stu-id="c3f8f-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="c3f8f-120">Determina se um especificado `IAssemblyName` objeto é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificado.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="c3f8f-121">Método SetProperty</span><span class="sxs-lookup"><span data-stu-id="c3f8f-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="c3f8f-122">Define o valor da propriedade referenciada pelo `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="c3f8f-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c3f8f-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c3f8f-123">Requirements</span></span>  
 <span data-ttu-id="c3f8f-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3f8f-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3f8f-125">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="c3f8f-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c3f8f-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3f8f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3f8f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3f8f-127">See also</span></span>

- [<span data-ttu-id="c3f8f-128">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="c3f8f-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [<span data-ttu-id="c3f8f-129">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="c3f8f-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
