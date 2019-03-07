---
title: Método IMetaDataImport::GetMethodProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 57604d80d40130ca147c026852b7bcd23f8f90bc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496450"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="b6a7e-102">Método IMetaDataImport::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="b6a7e-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="b6a7e-103">Obtém o token de metadados associados com o método referenciado pelo MethodDef especificado.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6a7e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6a7e-104">Syntax</span></span>  
  
```  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6a7e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b6a7e-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="b6a7e-106">[in] O token MethodDef que representa o método para retornar metadados.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="b6a7e-107">[out] Um ponteiro para um token de TypeDef que representa o tipo que implementa o método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="b6a7e-108">[out] Um ponteiro para um buffer que tem o nome do método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="b6a7e-109">[in] O tamanho solicitado do `szMethod`.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="b6a7e-110">[out] Um ponteiro para o tamanho em caracteres largos da `szMethod`, ou, no caso de truncamento, o número real de caracteres largos no nome do método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="b6a7e-111">[out] Um ponteiro para qualquer sinalizadores associados com o método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="b6a7e-112">[out] Um ponteiro para a assinatura de metadados de binários do método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="b6a7e-113">[out] Um ponteiro para o tamanho em bytes do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="b6a7e-114">[out] Um ponteiro para o endereço virtual relativo do método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="b6a7e-115">[out] Um ponteiro para os sinalizadores de implementação para o método.</span><span class="sxs-lookup"><span data-stu-id="b6a7e-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6a7e-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6a7e-116">Requirements</span></span>  
 <span data-ttu-id="b6a7e-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6a7e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6a7e-118">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b6a7e-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6a7e-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b6a7e-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6a7e-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6a7e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6a7e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6a7e-121">See also</span></span>
- [<span data-ttu-id="b6a7e-122">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="b6a7e-122">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b6a7e-123">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="b6a7e-123">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
