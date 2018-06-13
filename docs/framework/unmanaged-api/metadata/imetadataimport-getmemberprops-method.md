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
ms.openlocfilehash: d93763da2afbbdb1e738c802ba172e9f16e5f7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448452"
---
# <a name="imetadataimportgetmemberprops-method"></a><span data-ttu-id="35216-102">Método IMetaDataImport::GetMemberProps</span><span class="sxs-lookup"><span data-stu-id="35216-102">IMetaDataImport::GetMemberProps Method</span></span>
<span data-ttu-id="35216-103">Obtém informações de metadados, incluindo o nome, a assinatura binária e o endereço virtual relativo, do <xref:System.Type> membro referenciado pelo token de metadados especificado.</span><span class="sxs-lookup"><span data-stu-id="35216-103">Gets metadata information, including the name, binary signature, and relative virtual address, of the <xref:System.Type> member referenced by the specified metadata token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35216-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="35216-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="35216-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="35216-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="35216-106">[in] O token que referencia o membro para obter os metadados associados.</span><span class="sxs-lookup"><span data-stu-id="35216-106">[in] The token that references the member to get the associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="35216-107">[out] Um ponteiro para o token de metadados que representa a classe do membro.</span><span class="sxs-lookup"><span data-stu-id="35216-107">[out] A pointer to the metadata token that represents the class of the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="35216-108">[out] O nome do membro.</span><span class="sxs-lookup"><span data-stu-id="35216-108">[out] The name of the member.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="35216-109">[in] O tamanho em caracteres largos do `szMember` buffer.</span><span class="sxs-lookup"><span data-stu-id="35216-109">[in] The size in wide characters of the `szMember` buffer.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="35216-110">[out] O tamanho em caracteres largos do nome retornado.</span><span class="sxs-lookup"><span data-stu-id="35216-110">[out] The size in wide characters of the returned name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="35216-111">[out] Quaisquer valores de sinalizador aplicados ao membro.</span><span class="sxs-lookup"><span data-stu-id="35216-111">[out] Any flag values applied to the member.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="35216-112">[out] Um ponteiro para a assinatura de binários de metadados do membro.</span><span class="sxs-lookup"><span data-stu-id="35216-112">[out] A pointer to the binary metadata signature of the member.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="35216-113">[out] O tamanho em bytes do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="35216-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="35216-114">[out] Um ponteiro para o endereço virtual relativo do membro.</span><span class="sxs-lookup"><span data-stu-id="35216-114">[out] A pointer to the relative virtual address of the member.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="35216-115">[out] Os sinalizadores de implementação do método associados ao membro.</span><span class="sxs-lookup"><span data-stu-id="35216-115">[out] Any method implementation flags associated with the member.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="35216-116">[out] Um sinalizador que marca um <xref:System.ValueType>.</span><span class="sxs-lookup"><span data-stu-id="35216-116">[out] A flag that marks a <xref:System.ValueType>.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="35216-117">[out] Um valor de constante de cadeia de caracteres retornado por este membro.</span><span class="sxs-lookup"><span data-stu-id="35216-117">[out] A constant string value returned by this member.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="35216-118">[out] O tamanho em caracteres do `ppValue`, ou zero se `ppValue` não tem uma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="35216-118">[out] The size in characters of `ppValue`, or zero if `ppValue` does not hold a string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35216-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="35216-119">Requirements</span></span>  
 <span data-ttu-id="35216-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35216-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35216-121">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="35216-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="35216-122">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="35216-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="35216-123">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35216-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35216-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35216-124">See Also</span></span>  
 [<span data-ttu-id="35216-125">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="35216-125">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="35216-126">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="35216-126">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
