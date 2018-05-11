---
title: Interface IReferenceIdentity
ms.date: 03/30/2017
api_name:
- IReferenceIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IReferenceIdentity
helpviewer_keywords:
- IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4708fa173725e4c91a13f5b92cdbb1fdf8a8a4d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ireferenceidentity-interface"></a><span data-ttu-id="7f3ed-102">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="7f3ed-102">IReferenceIdentity Interface</span></span>
<span data-ttu-id="7f3ed-103">Representa uma referência para a assinatura exclusiva de um objeto de código.</span><span class="sxs-lookup"><span data-stu-id="7f3ed-103">Represents a reference to the unique signature of a code object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7f3ed-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="7f3ed-104">Methods</span></span>  
  
|<span data-ttu-id="7f3ed-105">Método</span><span class="sxs-lookup"><span data-stu-id="7f3ed-105">Method</span></span>|<span data-ttu-id="7f3ed-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f3ed-106">Description</span></span>|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|<span data-ttu-id="7f3ed-107">Obtém um ponteiro de interface para um novo `IReferenceIdentity` instância que é idêntica a esta `IReferenceIdentity`, exceto para as alterações de atributo especificado.</span><span class="sxs-lookup"><span data-stu-id="7f3ed-107">Gets an interface pointer to a new `IReferenceIdentity` instance that is identical to this `IReferenceIdentity`, except for the specified attribute changes.</span></span>|  
|`IReferenceIdentity::EnumAttributes`|<span data-ttu-id="7f3ed-108">Obtém um ponteiro de interface para um `IEnumIDENTITY_ATTRIBUTE` instância que contém os atributos associados a este `IReferenceIdentity`.</span><span class="sxs-lookup"><span data-stu-id="7f3ed-108">Gets an interface pointer to an `IEnumIDENTITY_ATTRIBUTE` instance that contains the attributes associated with this `IReferenceIdentity`.</span></span>|  
|`IReferenceIdentity::GetAttribute`|<span data-ttu-id="7f3ed-109">Obtém o valor do atributo no namespace especificado com o nome especificado.</span><span class="sxs-lookup"><span data-stu-id="7f3ed-109">Gets the value of the attribute in the specified namespace, with the specified name.</span></span>|  
|`IReferenceIdentity::SetAttribute`|<span data-ttu-id="7f3ed-110">Define o atributo que tem o namespace especificado e o nome especificado para o valor especificado.</span><span class="sxs-lookup"><span data-stu-id="7f3ed-110">Sets the attribute that has the specified namespace and the specified name to the specified value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f3ed-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f3ed-111">Requirements</span></span>  
 <span data-ttu-id="7f3ed-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f3ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f3ed-113">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="7f3ed-113">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7f3ed-114">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f3ed-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f3ed-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f3ed-115">See Also</span></span>  
 [<span data-ttu-id="7f3ed-116">Interfaces de fusão</span><span class="sxs-lookup"><span data-stu-id="7f3ed-116">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="7f3ed-117">Interface IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7f3ed-117">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
