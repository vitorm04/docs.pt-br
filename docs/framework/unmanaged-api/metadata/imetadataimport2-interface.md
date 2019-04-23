---
title: Interface IMetaDataImport2
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211915"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="fddbb-102">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fddbb-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="fddbb-103">Estende o [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para fornecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="fddbb-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fddbb-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="fddbb-104">Methods</span></span>  
  
|<span data-ttu-id="fddbb-105">Método</span><span class="sxs-lookup"><span data-stu-id="fddbb-105">Method</span></span>|<span data-ttu-id="fddbb-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="fddbb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fddbb-107">Método EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="fddbb-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="fddbb-108">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associado com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="fddbb-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="fddbb-109">Método EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="fddbb-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="fddbb-110">Obtém um enumerador para uma matriz genérica de tokens de parâmetro associados TypeDef especificado ou MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="fddbb-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="fddbb-111">Método EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="fddbb-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="fddbb-112">Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="fddbb-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="fddbb-113">Método GetGenericParamConstraintProps</span><span class="sxs-lookup"><span data-stu-id="fddbb-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="fddbb-114">Obtém os metadados associados com a restrição de parâmetro genérico representada pelo token de restrição especificada.</span><span class="sxs-lookup"><span data-stu-id="fddbb-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="fddbb-115">Método GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="fddbb-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="fddbb-116">Obtém os metadados associados com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="fddbb-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="fddbb-117">Método GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="fddbb-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="fddbb-118">Obtém o token de assinatura de metadados do método referenciado pelo MethodSpec especificado.</span><span class="sxs-lookup"><span data-stu-id="fddbb-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="fddbb-119">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="fddbb-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="fddbb-120">Obtém um valor que identifica a natureza do código em um arquivo executável portátil (PE) de arquivo, normalmente um arquivo DLL ou EXE, definido no escopo atual de metadados</span><span class="sxs-lookup"><span data-stu-id="fddbb-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="fddbb-121">Método GetVersionString</span><span class="sxs-lookup"><span data-stu-id="fddbb-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="fddbb-122">Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.</span><span class="sxs-lookup"><span data-stu-id="fddbb-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fddbb-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fddbb-123">Requirements</span></span>  
 <span data-ttu-id="fddbb-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fddbb-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fddbb-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fddbb-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fddbb-126">**Biblioteca:** Usado como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fddbb-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fddbb-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fddbb-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fddbb-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fddbb-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="fddbb-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="fddbb-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="fddbb-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fddbb-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
