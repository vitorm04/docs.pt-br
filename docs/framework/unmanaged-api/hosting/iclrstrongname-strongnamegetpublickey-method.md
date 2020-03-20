---
title: Método ICLRStrongName::StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181930"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="20439-102">Método ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="20439-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="20439-103">Obtém a chave pública de um par de chaves públicas/privadas.</span><span class="sxs-lookup"><span data-stu-id="20439-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="20439-104">O par de chaves pode ser fornecido como um nome de contêiner chave dentro de um provedor de serviços criptográficos (CSP) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="20439-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20439-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="20439-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20439-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="20439-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="20439-107">[em] O nome do recipiente de chave que contém o par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="20439-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="20439-108">Se `pbKeyBlob` for `szKeyContainer` nulo, deve especificar um recipiente válido dentro do CSP.</span><span class="sxs-lookup"><span data-stu-id="20439-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="20439-109">Neste caso, o método [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="20439-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="20439-110">Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).</span><span class="sxs-lookup"><span data-stu-id="20439-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="20439-111">As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="20439-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="20439-112">Nenhum outro tipo de chaves é suportado neste momento.</span><span class="sxs-lookup"><span data-stu-id="20439-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="20439-113">[em] Um ponteiro para o par de tecla público/privado.</span><span class="sxs-lookup"><span data-stu-id="20439-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="20439-114">Este par está no formato criado pela `CryptExportKey` função Win32.</span><span class="sxs-lookup"><span data-stu-id="20439-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="20439-115">Se `pbKeyBlob` for nulo, o `szKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="20439-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="20439-116">[em] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="20439-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="20439-117">[fora] A chave pública devolvida BLOB.</span><span class="sxs-lookup"><span data-stu-id="20439-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="20439-118">O `ppbPublicKeyBlob` parâmetro é alocado pelo tempo de execução do idioma comum e devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="20439-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="20439-119">O chamador deve liberar a memória usando o método [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="20439-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="20439-120">[fora] O tamanho da chave pública devolvida BLOB.</span><span class="sxs-lookup"><span data-stu-id="20439-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20439-121">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="20439-121">Return Value</span></span>  
 <span data-ttu-id="20439-122">`S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="20439-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="20439-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="20439-123">Remarks</span></span>  
 <span data-ttu-id="20439-124">A chave pública está contida em uma estrutura [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="20439-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20439-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="20439-125">Requirements</span></span>  
 <span data-ttu-id="20439-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20439-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20439-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="20439-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="20439-128">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="20439-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20439-129">**.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20439-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20439-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="20439-130">See also</span></span>

- [<span data-ttu-id="20439-131">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="20439-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="20439-132">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="20439-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="20439-133">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="20439-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
