---
title: Método IMetaDataEmit::DefineMemberRef
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMemberRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMemberRef
helpviewer_keywords:
- DefineMemberRef method [.NET Framework metadata]
- IMetaDataEmit::DefineMemberRef method [.NET Framework metadata]
ms.assetid: 21b5bcb8-ea75-4962-8acc-ad17584061e5
topic_type:
- apiref
ms.openlocfilehash: 576f4561ed782f091840ac378831110a1bfef9c6
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004681"
---
# <a name="imetadataemitdefinememberref-method"></a><span data-ttu-id="c5bff-102">Método IMetaDataEmit::DefineMemberRef</span><span class="sxs-lookup"><span data-stu-id="c5bff-102">IMetaDataEmit::DefineMemberRef Method</span></span>
<span data-ttu-id="c5bff-103">Define uma referência a um membro de um módulo fora do escopo atual e Obtém um token para essa definição de referência.</span><span class="sxs-lookup"><span data-stu-id="c5bff-103">Defines a reference to a member of a module outside the current scope, and gets a token to that reference definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5bff-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c5bff-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMemberRef (
    [in]  mdToken           tkImport,
    [in]  LPCWSTR           szName,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMemberRef       *pmr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5bff-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c5bff-105">Parameters</span></span>  
 `tkImport`  
 <span data-ttu-id="c5bff-106">no Token para a classe ou a interface do membro de destino, se o membro não for global; Se o membro for global, o `mdModuleRef` token para esse outro arquivo.</span><span class="sxs-lookup"><span data-stu-id="c5bff-106">[in] Token for the target member's class or interface, if the member is not global; if the member is global, the `mdModuleRef` token for that other file.</span></span>  
  
 `szName`  
 <span data-ttu-id="c5bff-107">no O nome do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="c5bff-107">[in] The name of the target member.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="c5bff-108">no A assinatura do membro de destino.</span><span class="sxs-lookup"><span data-stu-id="c5bff-108">[in] The signature of the target member.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="c5bff-109">no A contagem de bytes em `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="c5bff-109">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `pmr`  
 <span data-ttu-id="c5bff-110">fora O `mdMemberRef` token atribuído.</span><span class="sxs-lookup"><span data-stu-id="c5bff-110">[out] The `mdMemberRef` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5bff-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c5bff-111">Requirements</span></span>  
 <span data-ttu-id="c5bff-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5bff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5bff-113">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c5bff-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c5bff-114">**Biblioteca:** Usado como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c5bff-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5bff-115">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5bff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bff-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="c5bff-116">See also</span></span>

- [<span data-ttu-id="c5bff-117">Interface IMetaDataEmit</span><span class="sxs-lookup"><span data-stu-id="c5bff-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="c5bff-118">Interface IMetaDataEmit2</span><span class="sxs-lookup"><span data-stu-id="c5bff-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
