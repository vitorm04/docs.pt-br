---
title: Método IMetaDataImport::GetMemberProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberProps
helpviewer_keywords:
- IMetaDataImport::GetMemberProps method [.NET Framework metadata]
- GetMemberProps method [.NET Framework metadata]
ms.assetid: 42790918-4142-4938-b8f4-a56979a55846
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 40631a15bd07b5aa54488e5d3b99cee751e2e0bd
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56748330"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="ade19-102">Método IMetaDataImport::GetMemberProps</span><span class="sxs-lookup"><span data-stu-id="ade19-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="ade19-103">Obtém as informações armazenadas nos metadados para uma definição de membro especificado, incluindo o nome, a assinatura binária e o endereço virtual relativo, da <xref:System.Type> membro referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="ade19-103">Gets information stored in the metadata for a specified member definition, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span> <span data-ttu-id="ade19-104">Esse é um método auxiliar simples: se *mb* é um MethodDef, então **GetMethodProps** é chamado; se *mb* é um FieldDef, em seguida, **GetFieldProps** é chamado.</span><span class="sxs-lookup"><span data-stu-id="ade19-104">This is a simple helper method: if *mb* is a MethodDef, then **GetMethodProps** is called; if *mb* is a FieldDef, then **GetFieldProps** is called.</span></span> <span data-ttu-id="ade19-105">Consulte estes outros métodos para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="ade19-105">See these other methods for details.</span></span> 
  
## <a name="syntax"></a><span data-ttu-id="ade19-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ade19-106">Syntax</span></span>  
  
```  
HRESULT GetMemberProps (  
   [in]  mdToken           mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] DWORD             *pdwAttr,  
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] ULONG             *pulCodeRVA,   
   [out] DWORD             *pdwImplFlags,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ade19-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ade19-107">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="ade19-108">[in] O token que referencia o membro para obter os metadados associados para.</span><span class="sxs-lookup"><span data-stu-id="ade19-108">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="ade19-109">[out] Um ponteiro para o token de metadados que representa a classe do membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-109">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="ade19-110">[out] O nome do membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-110">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="ade19-111">[in] O tamanho em caracteres largos do `szMember` buffer.</span><span class="sxs-lookup"><span data-stu-id="ade19-111">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="ade19-112">[out] O tamanho em caracteres largos do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="ade19-112">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="ade19-113">[out] Quaisquer valores de sinalizador aplicados ao membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-113">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="ade19-114">[out] Um ponteiro para a assinatura binária metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-114">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="ade19-115">[out] O tamanho em bytes do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ade19-115">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="ade19-116">[out] Um ponteiro para o endereço virtual relativo do membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-116">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="ade19-117">[out] Os sinalizadores de implementação do método associados ao membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-117">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="ade19-118">[out] Um sinalizador que marca um <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="ade19-118">[out] A flag that marks a <xref:System.ValueType>.</span></span> <span data-ttu-id="ade19-119">Ele é um do `ELEMENT_TYPE_*` valores.</span><span class="sxs-lookup"><span data-stu-id="ade19-119">It is one of the `ELEMENT_TYPE_*` values.</span></span>
  
 `ppValue`  
 <span data-ttu-id="ade19-120">[out] Um valor de cadeia de caracteres constante retornado por este membro.</span><span class="sxs-lookup"><span data-stu-id="ade19-120">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="ade19-121">[out] O tamanho em caracteres de `ppValue`, ou zero se `ppValue` não mantém uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="ade19-121">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ade19-122">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ade19-122">Requirements</span></span>  
 <span data-ttu-id="ade19-123">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ade19-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ade19-124">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ade19-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ade19-125">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ade19-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ade19-126">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ade19-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ade19-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ade19-127">See also</span></span>
- [<span data-ttu-id="ade19-128">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="ade19-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="ade19-129">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="ade19-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
