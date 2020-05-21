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
ms.openlocfilehash: 5a20bde64830617090c92afe5fae3a603cf9103b
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763119"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a><span data-ttu-id="72519-102">Método ICLRStrongName::StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="72519-102">ICLRStrongName::StrongNameGetPublicKey Method</span></span>
<span data-ttu-id="72519-103">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="72519-103">Gets the public key from a public/private key pair.</span></span> <span data-ttu-id="72519-104">O par de chaves pode ser fornecido como um nome de contêiner de chave em um CSP (provedor de serviços de criptografia) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="72519-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72519-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72519-105">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72519-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72519-106">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="72519-107">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="72519-107">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="72519-108">Se `pbKeyBlob` for NULL, `szKeyContainer` deve especificar um contêiner válido no CSP.</span><span class="sxs-lookup"><span data-stu-id="72519-108">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="72519-109">Nesse caso, o método [ICLRStrongName:: StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="72519-109">In this case, the [ICLRStrongName::StrongNameGetPublicKey](iclrstrongname-strongnamegetpublickey-method.md) method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="72519-110">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="72519-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="72519-111">As chaves devem ter chaves de assinatura de 1024 bits Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="72519-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="72519-112">Não há suporte para nenhum outro tipo de chave no momento.</span><span class="sxs-lookup"><span data-stu-id="72519-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="72519-113">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="72519-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="72519-114">Esse par está no formato criado pela função do Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="72519-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="72519-115">Se `pbKeyBlob` for NULL, o contêiner de chave especificado por `szKeyContainer` será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="72519-115">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="72519-116">no O tamanho, em bytes, de `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="72519-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="72519-117">fora O BLOB de chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="72519-117">[out] The returned public key BLOB.</span></span> <span data-ttu-id="72519-118">O `ppbPublicKeyBlob` parâmetro é alocado pelo Common Language Runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="72519-118">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="72519-119">O chamador deve liberar a memória usando o método [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72519-119">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="72519-120">fora O tamanho do BLOB de chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="72519-120">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72519-121">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="72519-121">Return Value</span></span>  
 <span data-ttu-id="72519-122">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="72519-122">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72519-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="72519-123">Remarks</span></span>  
 <span data-ttu-id="72519-124">A chave pública está contida em uma estrutura [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="72519-124">The public key is contained in a [PublicKeyBlob](../strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72519-125">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72519-125">Requirements</span></span>  
 <span data-ttu-id="72519-126">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72519-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72519-127">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="72519-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="72519-128">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="72519-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72519-129">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72519-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72519-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="72519-130">See also</span></span>

- [<span data-ttu-id="72519-131">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="72519-131">StrongNameTokenFromPublicKey Method</span></span>](iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="72519-132">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="72519-132">PublicKeyBlob Structure</span></span>](../strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="72519-133">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="72519-133">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
