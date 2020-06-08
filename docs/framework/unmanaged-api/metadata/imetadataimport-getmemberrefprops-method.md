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
ms.openlocfilehash: 00693f1a87334620442e8865e76183b2dab68878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503608"
---
# <a name="imetadataimportgetmemberrefprops-method"></a><span data-ttu-id="4113f-102">Método IMetaDataImport::GetMemberRefProps</span><span class="sxs-lookup"><span data-stu-id="4113f-102">IMetaDataImport::GetMemberRefProps Method</span></span>
<span data-ttu-id="4113f-103">Obtém os metadados associados ao membro referenciado pelo token especificado.</span><span class="sxs-lookup"><span data-stu-id="4113f-103">Gets metadata associated with the member referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4113f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4113f-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="4113f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4113f-105">Parameters</span></span>  
 `mr`  
 <span data-ttu-id="4113f-106">no O token de MemberRef para o qual retornar metadados associados.</span><span class="sxs-lookup"><span data-stu-id="4113f-106">[in] The MemberRef token to return associated metadata for.</span></span>  
  
 `ptk`  
 <span data-ttu-id="4113f-107">fora Um TypeDef ou TypeRef ou um token TypeSpec que representa a classe que declara o membro ou um token ModuleRef que representa a classe do módulo que declara o membro ou um MethodDef que representa o membro.</span><span class="sxs-lookup"><span data-stu-id="4113f-107">[out] A TypeDef or TypeRef, or TypeSpec token that represents the class that declares the member, or a ModuleRef token that represents the module class that declares the member, or a MethodDef that represents the member.</span></span>  
  
 `szMember`  
 <span data-ttu-id="4113f-108">fora Um buffer de cadeia de caracteres para o nome do membro.</span><span class="sxs-lookup"><span data-stu-id="4113f-108">[out] A string buffer for the member's name.</span></span>  
  
 `cchMember`  
 <span data-ttu-id="4113f-109">no O tamanho solicitado em caracteres largos de `szMember` .</span><span class="sxs-lookup"><span data-stu-id="4113f-109">[in] The requested size in wide characters of `szMember`.</span></span>  
  
 `pchMember`  
 <span data-ttu-id="4113f-110">fora O tamanho retornado em caracteres largos de `szMember` .</span><span class="sxs-lookup"><span data-stu-id="4113f-110">[out] The returned size in wide characters of `szMember`.</span></span>  
  
 `ppvSibBlob`  
 <span data-ttu-id="4113f-111">fora Um ponteiro para a assinatura de metadados binários do membro.</span><span class="sxs-lookup"><span data-stu-id="4113f-111">[out] A pointer to the binary metadata signature for the member.</span></span>  
  
 `pbSig`  
 <span data-ttu-id="4113f-112">fora O tamanho em bytes de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="4113f-112">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4113f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4113f-113">Requirements</span></span>  
 <span data-ttu-id="4113f-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4113f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4113f-115">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4113f-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4113f-116">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4113f-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4113f-117">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4113f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4113f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="4113f-118">See also</span></span>

- [<span data-ttu-id="4113f-119">Interface IMetaDataImport</span><span class="sxs-lookup"><span data-stu-id="4113f-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="4113f-120">Interface IMetaDataImport2</span><span class="sxs-lookup"><span data-stu-id="4113f-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
