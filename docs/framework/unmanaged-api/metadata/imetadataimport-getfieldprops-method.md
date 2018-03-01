---
title: "Método IMetaDataImport::GetFieldProps"
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
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7785ea6beaa882e72d200ef559ba75538224091d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="0e966-102">Método IMetaDataImport::GetFieldProps</span><span class="sxs-lookup"><span data-stu-id="0e966-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="0e966-103">Obtém os metadados associados ao campo referenciado pelo FieldDef especificado token.</span><span class="sxs-lookup"><span data-stu-id="0e966-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e966-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e966-104">Syntax</span></span>  
  
```  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,   
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,   
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pcbSigBlob,   
   [out] DWORD             *pdwCPlusTypeFlag,   
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e966-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0e966-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="0e966-106">[in] Um token de FieldDef que representa os metadados associados para o campo.</span><span class="sxs-lookup"><span data-stu-id="0e966-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="0e966-107">[out] Um ponteiro para um token de TypeDef que representa o tipo da classe que o campo pertence.</span><span class="sxs-lookup"><span data-stu-id="0e966-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="0e966-108">[out] O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="0e966-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="0e966-109">[in] O tamanho em caracteres largos do buffer para *szField*.</span><span class="sxs-lookup"><span data-stu-id="0e966-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="0e966-110">[out] O tamanho real do buffer retornado.</span><span class="sxs-lookup"><span data-stu-id="0e966-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="0e966-111">[out] Sinalizadores associados com os metadados do campo.</span><span class="sxs-lookup"><span data-stu-id="0e966-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="0e966-112">[in] Um ponteiro para o valor binário de metadados que descreve o campo.</span><span class="sxs-lookup"><span data-stu-id="0e966-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="0e966-113">[out] O tamanho em bytes do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="0e966-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="0e966-114">[out] Um sinalizador que especifica o tipo de valor do campo.</span><span class="sxs-lookup"><span data-stu-id="0e966-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="0e966-115">[out] Um valor constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="0e966-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="0e966-116">[out] O tamanho em caracteres de `ppValue`, ou zero não se existir nenhuma cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="0e966-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e966-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0e966-117">Requirements</span></span>  
 <span data-ttu-id="0e966-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e966-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e966-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0e966-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0e966-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0e966-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0e966-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e966-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e966-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e966-122">See Also</span></span>  
 [<span data-ttu-id="0e966-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="0e966-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0e966-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="0e966-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
