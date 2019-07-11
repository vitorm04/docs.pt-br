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
ms.openlocfilehash: 981829500e499be05a8de7c1ffb4683429a903e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781857"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="abaf0-102">Enumeração CorGenericParamAttr</span><span class="sxs-lookup"><span data-stu-id="abaf0-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="abaf0-103">Contém valores que descrevem o <xref:System.Type> parâmetros de tipos genéricos, como usado em chamadas para [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="abaf0-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abaf0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abaf0-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="abaf0-105">Membros</span><span class="sxs-lookup"><span data-stu-id="abaf0-105">Members</span></span>  
  
|<span data-ttu-id="abaf0-106">Membro</span><span class="sxs-lookup"><span data-stu-id="abaf0-106">Member</span></span>|<span data-ttu-id="abaf0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="abaf0-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="abaf0-108">Variação de parâmetro se aplica somente aos parâmetros genéricos de interfaces e delegados.</span><span class="sxs-lookup"><span data-stu-id="abaf0-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="abaf0-109">Indica a ausência de variação.</span><span class="sxs-lookup"><span data-stu-id="abaf0-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="abaf0-110">Indica a covariância.</span><span class="sxs-lookup"><span data-stu-id="abaf0-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="abaf0-111">Indica a contravariância.</span><span class="sxs-lookup"><span data-stu-id="abaf0-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="abaf0-112">As restrições especiais podem aplicar a qualquer <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="abaf0-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="abaf0-113">Indica que nenhuma restrição se aplica para o <xref:System.Type> parâmetro.</span><span class="sxs-lookup"><span data-stu-id="abaf0-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="abaf0-114">Indica que o <xref:System.Type> parâmetro deve ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="abaf0-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="abaf0-115">Indica que o <xref:System.Type> parâmetro deve ser um tipo de valor não pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="abaf0-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="abaf0-116">Indica que o <xref:System.Type> parâmetro deve ter um construtor público padrão que não aceita parâmetros.</span><span class="sxs-lookup"><span data-stu-id="abaf0-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="abaf0-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="abaf0-117">Requirements</span></span>  
 <span data-ttu-id="abaf0-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abaf0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abaf0-119">**Cabeçalho:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="abaf0-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="abaf0-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abaf0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abaf0-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="abaf0-121">See also</span></span>

- [<span data-ttu-id="abaf0-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="abaf0-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
