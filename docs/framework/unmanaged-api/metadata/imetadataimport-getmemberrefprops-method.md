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
ms.openlocfilehash: a61254ba751e47b0089a3f7528aca337a32e2db3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175363"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="3185a-102">Método IMetaDataImport::GetMemberRefProps</span><span class="sxs-lookup"><span data-stu-id="3185a-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="3185a-103">Obtém metadados associados ao membro referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="3185a-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3185a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3185a-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="3185a-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="3185a-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="3185a-106">[em] O token MemberRef para retornar metadados associados para.</span><span class="sxs-lookup"><span data-stu-id="3185a-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="3185a-107">[fora] Um tipoDef ou TypeRef, ou token TypeSpec que representa a classe que declara o membro, ou um token ModuleRef que representa a classe de módulo que declara o membro, ou um MethodDef que representa o membro.</span><span class="sxs-lookup"><span data-stu-id="3185a-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="3185a-108">[fora] Um buffer de cordas para o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="3185a-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="3185a-109">[em] O tamanho solicitado em `szMember`caracteres amplos de .</span><span class="sxs-lookup"><span data-stu-id="3185a-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="3185a-110">[fora] O tamanho retornado em `szMember`caracteres largos de .</span><span class="sxs-lookup"><span data-stu-id="3185a-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="3185a-111">[fora] Um ponteiro para a assinatura binária de metadados para o membro.</span><span class="sxs-lookup"><span data-stu-id="3185a-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="3185a-112">[fora] O tamanho em bytes de `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="3185a-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3185a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3185a-113">Requirements</span></span>  
 <span data-ttu-id="3185a-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3185a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3185a-115">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3185a-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3185a-116">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3185a-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3185a-117">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3185a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3185a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="3185a-118">See also</span></span>

- [<span data-ttu-id="3185a-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="3185a-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3185a-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="3185a-120">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
