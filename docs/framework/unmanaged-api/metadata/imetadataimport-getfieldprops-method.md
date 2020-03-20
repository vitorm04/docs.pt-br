---
title: Método IMetaDataImport::GetFieldProps
ms.date: 03/30/2017
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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177240"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="fb37f-102">Método IMetaDataImport::GetFieldProps</span><span class="sxs-lookup"><span data-stu-id="fb37f-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="fb37f-103">Obtém metadados associados ao campo referenciado pelo token FieldDef especificado.</span><span class="sxs-lookup"><span data-stu-id="fb37f-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb37f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fb37f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="fb37f-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="fb37f-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="fb37f-106">[em] Um token FieldDef que representa o campo para obter metadados associados.</span><span class="sxs-lookup"><span data-stu-id="fb37f-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="fb37f-107">[fora] Um ponteiro para um token TypeDef que representa o tipo da classe a que o campo pertence.</span><span class="sxs-lookup"><span data-stu-id="fb37f-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="fb37f-108">[fora] O nome do campo.</span><span class="sxs-lookup"><span data-stu-id="fb37f-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="fb37f-109">[em] O tamanho em caracteres largos do buffer para *szField*.</span><span class="sxs-lookup"><span data-stu-id="fb37f-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="fb37f-110">[fora] O tamanho real do buffer devolvido.</span><span class="sxs-lookup"><span data-stu-id="fb37f-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="fb37f-111">[fora] Sinalizadores associados aos metadados do campo.</span><span class="sxs-lookup"><span data-stu-id="fb37f-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="fb37f-112">[em] Um ponteiro para o valor binário de metadados que descreve o campo.</span><span class="sxs-lookup"><span data-stu-id="fb37f-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="fb37f-113">[fora] O tamanho em bytes de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="fb37f-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="fb37f-114">[fora] Uma bandeira que especifica o tipo de valor do campo.</span><span class="sxs-lookup"><span data-stu-id="fb37f-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="fb37f-115">[fora] Um valor constante para o campo.</span><span class="sxs-lookup"><span data-stu-id="fb37f-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="fb37f-116">[fora] O tamanho em `ppValue`chars de , ou zero se não houver nenhuma corda.</span><span class="sxs-lookup"><span data-stu-id="fb37f-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb37f-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fb37f-117">Requirements</span></span>  
 <span data-ttu-id="fb37f-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb37f-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb37f-119">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fb37f-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fb37f-120">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fb37f-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fb37f-121">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb37f-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb37f-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb37f-122">See also</span></span>

- [<span data-ttu-id="fb37f-123">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="fb37f-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="fb37f-124">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="fb37f-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
