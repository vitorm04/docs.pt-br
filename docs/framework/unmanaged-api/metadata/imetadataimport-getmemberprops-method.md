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
ms.openlocfilehash: 98d7be5adc81cff09b121265e7d5b5f712122607
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611404"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="6b7f2-102">Método IMetaDataImport::GetMemberProps</span><span class="sxs-lookup"><span data-stu-id="6b7f2-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="6b7f2-103">Obtém informações de metadados, incluindo o nome, a assinatura binária e o endereço virtual relativo, da <xref:System.Type> membro referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b7f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6b7f2-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="6b7f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6b7f2-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="6b7f2-106">[in] O token que referencia o membro para obter os metadados associados para.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="6b7f2-107">[out] Um ponteiro para o token de metadados que representa a classe do membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="6b7f2-108">[out] O nome do membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="6b7f2-109">[in] O tamanho em caracteres largos do `szMember` buffer.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="6b7f2-110">[out] O tamanho em caracteres largos do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="6b7f2-111">[out] Quaisquer valores de sinalizador aplicados ao membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="6b7f2-112">[out] Um ponteiro para a assinatura binária metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="6b7f2-113">[out] O tamanho em bytes do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="6b7f2-114">[out] Um ponteiro para o endereço virtual relativo do membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="6b7f2-115">[out] Os sinalizadores de implementação do método associados ao membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="6b7f2-116">[out] Um sinalizador que marca um <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="6b7f2-117">[out] Um valor de cadeia de caracteres constante retornado por este membro.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="6b7f2-118">[out] O tamanho em caracteres de `ppValue`, ou zero se `ppValue` não mantém uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="6b7f2-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b7f2-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6b7f2-119">Requirements</span></span>  
 <span data-ttu-id="6b7f2-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b7f2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b7f2-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6b7f2-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6b7f2-122">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="6b7f2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6b7f2-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b7f2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b7f2-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b7f2-124">See also</span></span>
- [<span data-ttu-id="6b7f2-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="6b7f2-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="6b7f2-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="6b7f2-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
