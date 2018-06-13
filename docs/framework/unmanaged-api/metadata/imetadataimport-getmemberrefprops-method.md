---
title: Método IMetaDataImport::GetMemberRefProps
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMemberRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMemberRefProps
helpviewer_keywords:
- GetMemberRefProps method [.NET Framework metadata]
- IMetaDataImport::GetMemberRefProps method [.NET Framework metadata]
ms.assetid: 0ea73055-ece0-4151-a094-414c88ef8941
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0d62b9be1bef16014e2870c15a232bb46d4daf10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448738"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="a49d7-102">Método IMetaDataImport::GetMemberRefProps</span><span class="sxs-lookup"><span data-stu-id="a49d7-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="a49d7-103">Obtém os metadados associados ao membro referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="a49d7-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a49d7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a49d7-104">Syntax</span></span>  
  
```  
HRESULT GetMemberRefProps (  
   [in]  mdMemberRef       mr,   
   [out] mdToken           *ptk,   
   [out] LPWSTR            szMember,   
   [in]  ULONG             cchMember,   
   [out] ULONG             *pchMember,   
   [out] PCCOR_SIGNATURE   *ppvSigBlob,   
   [out] ULONG             *pbSig   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a49d7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a49d7-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="a49d7-106">[in] O token de MemberRef para retornar os metadados associados.</span><span class="sxs-lookup"><span data-stu-id="a49d7-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="a49d7-107">[out] Um token de TypeDef ou TypeRef ou TypeSpec que representa a classe que declara o membro ou um token de ModuleRef que representa a classe de módulo que declara o membro ou um MethodDef que representa o membro.</span><span class="sxs-lookup"><span data-stu-id="a49d7-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="a49d7-108">[out] Um buffer de cadeia de caracteres para o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="a49d7-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="a49d7-109">[in] O tamanho solicitado em caracteres largos de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="a49d7-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="a49d7-110">[out] O tamanho retornado em caracteres largos de `szMember`.</span><span class="sxs-lookup"><span data-stu-id="a49d7-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="a49d7-111">[out] Um ponteiro para a assinatura de binários de metadados para o membro.</span><span class="sxs-lookup"><span data-stu-id="a49d7-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="a49d7-112">[out] O tamanho em bytes do `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="a49d7-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a49d7-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a49d7-113">Requirements</span></span>  
 <span data-ttu-id="a49d7-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a49d7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a49d7-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a49d7-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a49d7-116">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="a49d7-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a49d7-117">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a49d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49d7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a49d7-118">See Also</span></span>  
 [<span data-ttu-id="a49d7-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="a49d7-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="a49d7-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="a49d7-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
