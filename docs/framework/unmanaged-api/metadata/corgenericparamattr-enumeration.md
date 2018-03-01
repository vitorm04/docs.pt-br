---
title: "Enumeração CorGenericParamAttr"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e40613d790baed5bd89bee1e1f5ca57043bfe76a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="f52bf-102">Enumeração CorGenericParamAttr</span><span class="sxs-lookup"><span data-stu-id="f52bf-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="f52bf-103">Contém valores que descrevem o <xref:System.Type> parâmetros para tipos genéricos, como usado em chamadas para [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="f52bf-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f52bf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f52bf-104">Syntax</span></span>  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="f52bf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f52bf-105">Members</span></span>  
  
|<span data-ttu-id="f52bf-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f52bf-106">Member</span></span>|<span data-ttu-id="f52bf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f52bf-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="f52bf-108">Variação de parâmetro só se aplica a parâmetros genéricos para interfaces e delegados.</span><span class="sxs-lookup"><span data-stu-id="f52bf-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="f52bf-109">Indica a ausência de variação.</span><span class="sxs-lookup"><span data-stu-id="f52bf-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="f52bf-110">Indica a covariância.</span><span class="sxs-lookup"><span data-stu-id="f52bf-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="f52bf-111">Indica contravariância.</span><span class="sxs-lookup"><span data-stu-id="f52bf-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="f52bf-112">Restrições especiais podem aplicar a qualquer <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f52bf-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="f52bf-113">Indica que nenhuma restrição se aplica ao <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f52bf-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="f52bf-114">Indica que o <xref:System.Type> parâmetro deve ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="f52bf-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="f52bf-115">Indica que o <xref:System.Type> parâmetro deve ser um tipo de valor não pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="f52bf-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="f52bf-116">Indica que o <xref:System.Type> parâmetro deve ter um construtor público padrão que não usa nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="f52bf-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f52bf-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f52bf-117">Requirements</span></span>  
 <span data-ttu-id="f52bf-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f52bf-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f52bf-119">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="f52bf-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f52bf-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f52bf-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f52bf-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f52bf-121">See Also</span></span>  
 [<span data-ttu-id="f52bf-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="f52bf-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
