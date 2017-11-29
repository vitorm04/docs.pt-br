---
title: "Enumeração CorGenericParamAttr"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGenericParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGenericParamAttr
helpviewer_keywords: CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95d7a6097766c8e2389e9828f54e81e37ffea454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="5a377-102">Enumeração CorGenericParamAttr</span><span class="sxs-lookup"><span data-stu-id="5a377-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="5a377-103">Contém valores que descrevem o <xref:System.Type> parâmetros para tipos genéricos, como usado em chamadas para [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="5a377-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a377-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a377-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="5a377-105">Membros</span><span class="sxs-lookup"><span data-stu-id="5a377-105">Members</span></span>  
  
|<span data-ttu-id="5a377-106">Membro</span><span class="sxs-lookup"><span data-stu-id="5a377-106">Member</span></span>|<span data-ttu-id="5a377-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a377-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="5a377-108">Variação de parâmetro só se aplica a parâmetros genéricos para interfaces e delegados.</span><span class="sxs-lookup"><span data-stu-id="5a377-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="5a377-109">Indica a ausência de variação.</span><span class="sxs-lookup"><span data-stu-id="5a377-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="5a377-110">Indica a covariância.</span><span class="sxs-lookup"><span data-stu-id="5a377-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="5a377-111">Indica contravariância.</span><span class="sxs-lookup"><span data-stu-id="5a377-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="5a377-112">Restrições especiais podem aplicar a qualquer <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5a377-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="5a377-113">Indica que nenhuma restrição se aplica ao <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5a377-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="5a377-114">Indica que o <xref:System.Type> parâmetro deve ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="5a377-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="5a377-115">Indica que o <xref:System.Type> parâmetro deve ser um tipo de valor não pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="5a377-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="5a377-116">Indica que o <xref:System.Type> parâmetro deve ter um construtor público padrão que não usa nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5a377-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5a377-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5a377-117">Requirements</span></span>  
 <span data-ttu-id="5a377-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a377-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a377-119">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="5a377-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="5a377-120">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a377-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a377-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a377-121">See Also</span></span>  
 [<span data-ttu-id="5a377-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="5a377-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
