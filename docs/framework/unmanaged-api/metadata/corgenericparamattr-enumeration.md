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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450283"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="d7974-102">Enumeração CorGenericParamAttr</span><span class="sxs-lookup"><span data-stu-id="d7974-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="d7974-103">Contém valores que descrevem os parâmetros de <xref:System.Type> para tipos genéricos, conforme usado em chamadas para [IMetaDataEmit2::D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="d7974-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7974-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7974-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d7974-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d7974-105">Members</span></span>  
  
|<span data-ttu-id="d7974-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d7974-106">Member</span></span>|<span data-ttu-id="d7974-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7974-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="d7974-108">A variação de parâmetro aplica-se somente a parâmetros genéricos para interfaces e delegados.</span><span class="sxs-lookup"><span data-stu-id="d7974-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="d7974-109">Indica a ausência de variação.</span><span class="sxs-lookup"><span data-stu-id="d7974-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="d7974-110">Indica covariância.</span><span class="sxs-lookup"><span data-stu-id="d7974-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="d7974-111">Indica contravariância.</span><span class="sxs-lookup"><span data-stu-id="d7974-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="d7974-112">Restrições especiais podem ser aplicadas a qualquer parâmetro de <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d7974-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="d7974-113">Indica que nenhuma restrição se aplica ao parâmetro <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="d7974-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="d7974-114">Indica que o parâmetro de <xref:System.Type> deve ser um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="d7974-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="d7974-115">Indica que o parâmetro de <xref:System.Type> deve ser um tipo de valor que não pode ser um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="d7974-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="d7974-116">Indica que o parâmetro <xref:System.Type> deve ter um construtor público padrão que não aceite parâmetros.</span><span class="sxs-lookup"><span data-stu-id="d7974-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7974-117">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d7974-117">Requirements</span></span>  
 <span data-ttu-id="d7974-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7974-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7974-119">**Cabeçalho:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="d7974-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d7974-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7974-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7974-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7974-121">See also</span></span>

- [<span data-ttu-id="d7974-122">Enumerações de metadados</span><span class="sxs-lookup"><span data-stu-id="d7974-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
