---
title: Interface IMetaDataImport2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2
helpviewer_keywords: IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1b00879f1d22d49e5f0dc3bdb072e0545feda68d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="4466b-102">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4466b-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="4466b-103">Estende o [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface para fornecer a capacidade de trabalhar com tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="4466b-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4466b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4466b-104">Methods</span></span>  
  
|<span data-ttu-id="4466b-105">Método</span><span class="sxs-lookup"><span data-stu-id="4466b-105">Method</span></span>|<span data-ttu-id="4466b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4466b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4466b-107">Método EnumGenericParamConstraints</span><span class="sxs-lookup"><span data-stu-id="4466b-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="4466b-108">Obtém um enumerador para uma matriz de restrições de parâmetro genérico associadas com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="4466b-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="4466b-109">Método EnumGenericParams</span><span class="sxs-lookup"><span data-stu-id="4466b-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="4466b-110">Obtém um enumerador para uma matriz de parâmetro genérico tokens associado com o TypeDef especificado ou MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="4466b-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="4466b-111">Método EnumMethodSpecs</span><span class="sxs-lookup"><span data-stu-id="4466b-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="4466b-112">Obtém um enumerador para uma matriz de tokens MethodSpec associados com a especificada MethodDef ou MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="4466b-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="4466b-113">Método GetGenericParamConstraintProps</span><span class="sxs-lookup"><span data-stu-id="4466b-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="4466b-114">Obtém os metadados associados com a restrição de parâmetro genérico representada pelo token de restrição especificada.</span><span class="sxs-lookup"><span data-stu-id="4466b-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="4466b-115">Método GetGenericParamProps</span><span class="sxs-lookup"><span data-stu-id="4466b-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="4466b-116">Obtém os metadados associados com o parâmetro genérico representado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="4466b-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="4466b-117">Método GetMethodSpecProps</span><span class="sxs-lookup"><span data-stu-id="4466b-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="4466b-118">Obtém a assinatura de metadados do método referenciado pelo MethodSpec especificado de token.</span><span class="sxs-lookup"><span data-stu-id="4466b-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="4466b-119">Método GetPEKind</span><span class="sxs-lookup"><span data-stu-id="4466b-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="4466b-120">Obtém um valor que identifica a natureza do código em um PE (executável portátil) de arquivo, geralmente um arquivo DLL ou EXE, definido no escopo atual de metadados</span><span class="sxs-lookup"><span data-stu-id="4466b-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="4466b-121">Método GetVersionString</span><span class="sxs-lookup"><span data-stu-id="4466b-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="4466b-122">Obtém o número de versão do tempo de execução que foi usado para compilar o assembly.</span><span class="sxs-lookup"><span data-stu-id="4466b-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4466b-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4466b-123">Requirements</span></span>  
 <span data-ttu-id="4466b-124">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4466b-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4466b-125">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="4466b-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4466b-126">**Biblioteca:** usado como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="4466b-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4466b-127">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4466b-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4466b-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4466b-128">See Also</span></span>  
 <xref:System.Reflection.PortableExecutableKinds>  
 [<span data-ttu-id="4466b-129">Interfaces de metadados</span><span class="sxs-lookup"><span data-stu-id="4466b-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [<span data-ttu-id="4466b-130">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4466b-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
