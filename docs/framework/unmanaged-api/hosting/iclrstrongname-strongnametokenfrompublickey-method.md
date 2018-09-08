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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98c0dbbbe65d8f8c0b0196c82db1a8fd2b0ee3dd
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44134487"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a><span data-ttu-id="fca8e-102">Método ICLRStrongName::StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="fca8e-102">ICLRStrongName::StrongNameTokenFromPublicKey Method</span></span>
<span data-ttu-id="fca8e-103">Obtém um token que representa uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="fca8e-103">Gets a token that represents a public key.</span></span> <span data-ttu-id="fca8e-104">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="fca8e-104">A strong name token is the shortened form of a public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca8e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fca8e-105">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fca8e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fca8e-106">Parameters</span></span>  
 `pbPublicKeyBlob`  
 <span data-ttu-id="fca8e-107">[in] Uma estrutura do tipo [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) que contém a parte pública do par de chaves usado para gerar a assinatura de nome forte.</span><span class="sxs-lookup"><span data-stu-id="fca8e-107">[in] A structure of type [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) that contains the public portion of the key pair used to generate the strong name signature.</span></span>  
  
 `cbPublicKeyBlob`  
 <span data-ttu-id="fca8e-108">[in] O tamanho, em bytes, do `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="fca8e-108">[in] The size, in bytes, of `pbPublicKeyBlob`.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="fca8e-109">[out] O token de nome forte correspondente à chave passada `pbPublicKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="fca8e-109">[out] The strong name token corresponding to the key passed in `pbPublicKeyBlob`.</span></span> <span data-ttu-id="fca8e-110">O common language runtime aloca a memória no qual retornar o token.</span><span class="sxs-lookup"><span data-stu-id="fca8e-110">The common language runtime allocates the memory in which to return the token.</span></span> <span data-ttu-id="fca8e-111">O chamador deve liberar essa memória usando o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="fca8e-111">The caller must free this memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="fca8e-112">[out] O tamanho, em bytes, do token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="fca8e-112">[out] The size, in bytes, of the returned strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fca8e-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fca8e-113">Return Value</span></span>  
 <span data-ttu-id="fca8e-114">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="fca8e-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fca8e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="fca8e-115">Remarks</span></span>  
 <span data-ttu-id="fca8e-116">Um token de nome forte é a forma abreviada de uma chave pública que é usada para economizar espaço ao armazenar informações de chave nos metadados.</span><span class="sxs-lookup"><span data-stu-id="fca8e-116">A strong name token is the shortened form of a public key that is used to save space when storing key information in metadata.</span></span> <span data-ttu-id="fca8e-117">Especificamente, os tokens de nome forte são usados nas referências de assembly para fazer referência ao assembly dependente.</span><span class="sxs-lookup"><span data-stu-id="fca8e-117">Specifically, strong name tokens are used in assembly references to refer to the dependent assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fca8e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fca8e-118">Requirements</span></span>  
 <span data-ttu-id="fca8e-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fca8e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca8e-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fca8e-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fca8e-121">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fca8e-121">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="fca8e-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fca8e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca8e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fca8e-123">See Also</span></span>  
 [<span data-ttu-id="fca8e-124">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="fca8e-124">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="fca8e-125">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="fca8e-125">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="fca8e-126">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fca8e-126">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
