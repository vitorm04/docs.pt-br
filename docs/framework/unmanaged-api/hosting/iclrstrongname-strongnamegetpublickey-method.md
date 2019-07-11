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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1d98ada710771029e92ae2a942105e361a6ac7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747971"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="f1362-102">Método ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="f1362-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="f1362-103">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="f1362-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="f1362-104">O par de chaves pode ser fornecido como um nome de contêiner de chave dentro de um provedor de serviços de criptografia (CSP) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="f1362-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1362-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1362-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1362-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1362-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="f1362-107">[in] O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="f1362-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="f1362-108">Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido dentro do CSP.</span><span class="sxs-lookup"><span data-stu-id="f1362-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="f1362-109">Nesse caso, o [iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) método extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="f1362-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="f1362-110">Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="f1362-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f1362-111">As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="f1362-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f1362-112">Não há outros tipos de chaves têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="f1362-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f1362-113">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="f1362-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f1362-114">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="f1362-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f1362-115">Se `pbKeyBlob` for nula, o contêiner de chave especificado por `szKeyContainer` deve para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="f1362-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f1362-116">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f1362-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="f1362-117">[out] A chave pública retornada BLOB.</span><span class="sxs-lookup"><span data-stu-id="f1362-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="f1362-118">O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="f1362-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="f1362-119">O chamador deve liberar a memória usando o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="f1362-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="f1362-120">[out] O tamanho da chave pública retornado BLOB.</span><span class="sxs-lookup"><span data-stu-id="f1362-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1362-121">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f1362-121">Return Value</span></span>  
 <span data-ttu-id="f1362-122">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="f1362-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1362-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1362-123">Remarks</span></span>  
 <span data-ttu-id="f1362-124">A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="f1362-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1362-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1362-125">Requirements</span></span>  
 <span data-ttu-id="f1362-126">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1362-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1362-127">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f1362-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f1362-128">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f1362-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1362-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1362-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1362-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1362-130">See also</span></span>

- [<span data-ttu-id="f1362-131">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="f1362-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="f1362-132">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="f1362-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="f1362-133">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f1362-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
