---
title: Método ICLRStrongName::StrongNameTokenFromPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: 13c1c505d939c1048eebef3d1d6b2abe493d319e
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937415"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="14ef2-102">Método ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="14ef2-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="14ef2-103">Obtém um token que representa uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="14ef2-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="14ef2-104">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="14ef2-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14ef2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14ef2-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14ef2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14ef2-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="14ef2-107">no Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="14ef2-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="14ef2-108">no O tamanho, em bytes, de `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="14ef2-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="14ef2-109">fora O token de nome forte correspondente à chave passada em `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="14ef2-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="14ef2-110">O Common Language Runtime aloca a memória na qual retornar o token.</span><span class="sxs-lookup"><span data-stu-id="14ef2-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="14ef2-111">O chamador deve liberar essa memória usando o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="14ef2-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="14ef2-112">fora O tamanho, em bytes, do token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="14ef2-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14ef2-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="14ef2-113">Return Value</span></span>  
 <span data-ttu-id="14ef2-114">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="14ef2-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14ef2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="14ef2-115">Remarks</span></span>  
 <span data-ttu-id="14ef2-116">Um token de nome forte é a forma abreviada de uma chave pública que é usada para economizar espaço ao armazenar informações de chave em metadados.</span><span class="sxs-lookup"><span data-stu-id="14ef2-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="14ef2-117">Especificamente, tokens de nome forte são usados em referências de assembly para fazer referência ao assembly dependente.</span><span class="sxs-lookup"><span data-stu-id="14ef2-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14ef2-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="14ef2-118">Requirements</span></span>  
 <span data-ttu-id="14ef2-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14ef2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14ef2-120">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="14ef2-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="14ef2-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="14ef2-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="14ef2-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14ef2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14ef2-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="14ef2-123">See also</span></span>

- [<span data-ttu-id="14ef2-124">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="14ef2-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="14ef2-125">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="14ef2-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="14ef2-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="14ef2-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
