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
ms.openlocfilehash: aa12252c4f2a8e710a4a880af103aa324f8118ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432394"
---
# <a name="iassemblyname-interface"></a><span data-ttu-id="4a056-102">Interface IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="4a056-102">IAssemblyName Interface</span></span>
<span data-ttu-id="4a056-103">Fornece métodos para descrever e trabalhar com uma identidade exclusiva de assembly.</span><span class="sxs-lookup"><span data-stu-id="4a056-103">Provides methods for describing and working with an assembly's unique identity.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a056-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4a056-104">Methods</span></span>  
  
|<span data-ttu-id="4a056-105">Método</span><span class="sxs-lookup"><span data-stu-id="4a056-105">Method</span></span>|<span data-ttu-id="4a056-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a056-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a056-107">Método Clone</span><span class="sxs-lookup"><span data-stu-id="4a056-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|<span data-ttu-id="4a056-108">Cria uma cópia superficial deste `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="4a056-108">Creates a shallow copy of this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4a056-109">Método Finalize</span><span class="sxs-lookup"><span data-stu-id="4a056-109">Finalize Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|<span data-ttu-id="4a056-110">Permite que este `IAssemblyName` objeto para liberar recursos e executar outras operações de limpeza antes do destruidor é chamado.</span><span class="sxs-lookup"><span data-stu-id="4a056-110">Allows this `IAssemblyName` object to release resources and perform other cleanup operations before its destructor is called.</span></span>|  
|[<span data-ttu-id="4a056-111">Método GetDisplayName</span><span class="sxs-lookup"><span data-stu-id="4a056-111">GetDisplayName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|<span data-ttu-id="4a056-112">Obtém o nome legível do assembly referenciado por essa `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="4a056-112">Gets the human-readable name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4a056-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="4a056-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|<span data-ttu-id="4a056-114">Obtém o nome simple, não criptografado do assembly referenciado por essa `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="4a056-114">Gets the simple, unencrypted name of the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4a056-115">Método GetProperty</span><span class="sxs-lookup"><span data-stu-id="4a056-115">GetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|<span data-ttu-id="4a056-116">Obtém um ponteiro para a propriedade referenciada pelo `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="4a056-116">Gets a pointer to the property referenced by the specified `PropertyId`.</span></span>|  
|[<span data-ttu-id="4a056-117">Método GetVersion</span><span class="sxs-lookup"><span data-stu-id="4a056-117">GetVersion Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|<span data-ttu-id="4a056-118">Obtém as informações de versão do assembly referenciado por essa `IAssemblyName` objeto.</span><span class="sxs-lookup"><span data-stu-id="4a056-118">Gets the version information for the assembly referenced by this `IAssemblyName` object.</span></span>|  
|[<span data-ttu-id="4a056-119">Método IsEqual</span><span class="sxs-lookup"><span data-stu-id="4a056-119">IsEqual Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|<span data-ttu-id="4a056-120">Determina se um especificado `IAssemblyName` objeto é igual a este `IAssemblyName`, com base nos sinalizadores de comparação especificado.</span><span class="sxs-lookup"><span data-stu-id="4a056-120">Determines whether a specified `IAssemblyName` object is equal to this `IAssemblyName`, based on the specified comparison flags.</span></span>|  
|[<span data-ttu-id="4a056-121">Método SetProperty</span><span class="sxs-lookup"><span data-stu-id="4a056-121">SetProperty Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|<span data-ttu-id="4a056-122">Define o valor da propriedade referenciada pelo `PropertyId`.</span><span class="sxs-lookup"><span data-stu-id="4a056-122">Sets the value of the property referenced by the specified `PropertyId`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a056-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4a056-123">Requirements</span></span>  
 <span data-ttu-id="4a056-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a056-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a056-125">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="4a056-125">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="4a056-126">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a056-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a056-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a056-127">See Also</span></span>  
 [<span data-ttu-id="4a056-128">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="4a056-128">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="4a056-129">Interface IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="4a056-129">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
