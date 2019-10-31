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
ms.openlocfilehash: 943251357a91ea9ae3d492fa7bf20eebf948b8b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135072"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="68288-102">Método ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="68288-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="68288-103">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="68288-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="68288-104">O par de chaves pode ser fornecido como um nome de contêiner de chave em um CSP (provedor de serviços de criptografia) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="68288-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68288-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68288-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68288-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="68288-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="68288-107">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="68288-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="68288-108">Se `pbKeyBlob` for NULL, `szKeyContainer` deverá especificar um contêiner válido no CSP.</span><span class="sxs-lookup"><span data-stu-id="68288-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="68288-109">Nesse caso, o método [ICLRStrongName:: StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="68288-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="68288-110">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="68288-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="68288-111">As chaves devem ter chaves de assinatura de 1024 bits Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="68288-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="68288-112">Não há suporte para nenhum outro tipo de chave no momento.</span><span class="sxs-lookup"><span data-stu-id="68288-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="68288-113">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="68288-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="68288-114">Esse par está no formato criado pela função de `CryptExportKey` do Win32.</span><span class="sxs-lookup"><span data-stu-id="68288-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="68288-115">Se `pbKeyBlob` for NULL, o contêiner de chave especificado por `szKeyContainer` será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="68288-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="68288-116">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="68288-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="68288-117">fora O BLOB de chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="68288-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="68288-118">O parâmetro `ppbPublicKeyBlob` é alocado pelo Common Language Runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="68288-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="68288-119">O chamador deve liberar a memória usando o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="68288-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="68288-120">fora O tamanho do BLOB de chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="68288-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68288-121">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="68288-121">Return Value</span></span>  
 <span data-ttu-id="68288-122">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="68288-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68288-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="68288-123">Remarks</span></span>  
 <span data-ttu-id="68288-124">A chave pública está contida em uma estrutura [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="68288-124">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68288-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="68288-125">Requirements</span></span>  
 <span data-ttu-id="68288-126">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68288-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68288-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="68288-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="68288-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="68288-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68288-129">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68288-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68288-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68288-130">See also</span></span>

- [<span data-ttu-id="68288-131">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="68288-131">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="68288-132">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="68288-132">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="68288-133">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="68288-133">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
