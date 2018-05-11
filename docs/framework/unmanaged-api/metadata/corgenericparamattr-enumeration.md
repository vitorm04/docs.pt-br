---
title: Enumeração CorGenericParamAttr
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d56be8c6f224010da22803894524299c0d376ba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="cf951-102">Enumeração CorGenericParamAttr</span><span class="sxs-lookup"><span data-stu-id="cf951-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="cf951-103">Contém valores que descrevem o <xref:System.Type> parâmetros para tipos genéricos, como usado em chamadas para [Imetadataemit2](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="cf951-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf951-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf951-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="cf951-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cf951-105">Members</span></span>  
  
|<span data-ttu-id="cf951-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cf951-106">Member</span></span>|<span data-ttu-id="cf951-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cf951-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="cf951-108">Variação de parâmetro só se aplica a parâmetros genéricos para interfaces e delegados.</span><span class="sxs-lookup"><span data-stu-id="cf951-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="cf951-109">Indica a ausência de variação.</span><span class="sxs-lookup"><span data-stu-id="cf951-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="cf951-110">Indica a covariância.</span><span class="sxs-lookup"><span data-stu-id="cf951-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="cf951-111">Indica contravariância.</span><span class="sxs-lookup"><span data-stu-id="cf951-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="cf951-112">Restrições especiais podem aplicar a qualquer <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf951-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="cf951-113">Indica que nenhuma restrição se aplica ao <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf951-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="cf951-114">Indica que o <xref:System.Type> parâmetro deve ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="cf951-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="cf951-115">Indica que o <xref:System.Type> parâmetro deve ser um tipo de valor não pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="cf951-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="cf951-116">Indica que o <xref:System.Type> parâmetro deve ter um construtor público padrão que não usa nenhum parâmetro.</span><span class="sxs-lookup"><span data-stu-id="cf951-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cf951-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf951-117">Requirements</span></span>  
 <span data-ttu-id="cf951-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf951-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf951-119">**Cabeçalho:** Corhdr</span><span class="sxs-lookup"><span data-stu-id="cf951-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cf951-120">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf951-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf951-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf951-121">See Also</span></span>  
 [<span data-ttu-id="cf951-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="cf951-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
