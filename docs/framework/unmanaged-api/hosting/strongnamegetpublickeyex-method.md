---
title: Método StrongNameGetPublicKeyEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176221"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="9845b-102">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="9845b-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="9845b-103">Obtém a chave pública de um par de chaves público/privado e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="9845b-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9845b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9845b-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9845b-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="9845b-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="9845b-106">[em] O nome do recipiente de chave que contém o par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="9845b-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="9845b-107">Se `pbKeyBlob` for `szKeyContainer` nulo, deve especificar um contêiner válido dentro do provedor de serviços criptográficos (CSP).</span><span class="sxs-lookup"><span data-stu-id="9845b-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="9845b-108">Neste caso, `StrongNameGetPublicKeyEx` o método extrai a chave pública do par de chaves armazenado no recipiente.</span><span class="sxs-lookup"><span data-stu-id="9845b-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="9845b-109">Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).</span><span class="sxs-lookup"><span data-stu-id="9845b-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="9845b-110">As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="9845b-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="9845b-111">Nenhum outro tipo de chaves é suportado neste momento.</span><span class="sxs-lookup"><span data-stu-id="9845b-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="9845b-112">[em] Um ponteiro para o par de tecla público/privado.</span><span class="sxs-lookup"><span data-stu-id="9845b-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="9845b-113">Este par está no formato criado pela `CryptExportKey` função Win32.</span><span class="sxs-lookup"><span data-stu-id="9845b-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="9845b-114">Se `pbKeyBlob` for nulo, o `szKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="9845b-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="9845b-115">[em] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="9845b-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="9845b-116">[fora] A chave pública devolvida BLOB.</span><span class="sxs-lookup"><span data-stu-id="9845b-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="9845b-117">O `ppbPublicKeyBlob` parâmetro é alocado pelo tempo de execução do idioma comum e devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="9845b-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="9845b-118">O chamador deve liberar a memória usando o método [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="9845b-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="9845b-119">[fora] O tamanho da chave pública devolvida BLOB.</span><span class="sxs-lookup"><span data-stu-id="9845b-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="9845b-120">[em] O algoritmo de hash da montagem.</span><span class="sxs-lookup"><span data-stu-id="9845b-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="9845b-121">Consulte a seção Observações para obter uma lista de valores aceitos.</span><span class="sxs-lookup"><span data-stu-id="9845b-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="9845b-122">[em] Reservado para uso futuro; padrões para nulo.</span><span class="sxs-lookup"><span data-stu-id="9845b-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9845b-123">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9845b-123">Return Value</span></span>  
 <span data-ttu-id="9845b-124">`S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="9845b-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9845b-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="9845b-125">Remarks</span></span>  
 <span data-ttu-id="9845b-126">A chave pública está contida em uma estrutura [PublicKeyBlob.](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="9845b-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9845b-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="9845b-127">Remarks</span></span>  
 <span data-ttu-id="9845b-128">A tabela a seguir mostra o `uHashAlgId` conjunto de valores aceitos para o parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9845b-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="9845b-129">Nome</span><span class="sxs-lookup"><span data-stu-id="9845b-129">Name</span></span>|<span data-ttu-id="9845b-130">Valor</span><span class="sxs-lookup"><span data-stu-id="9845b-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="9845b-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9845b-131">None</span></span>|<span data-ttu-id="9845b-132">0</span><span class="sxs-lookup"><span data-stu-id="9845b-132">0</span></span>|  
|<span data-ttu-id="9845b-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="9845b-133">SHA-1</span></span>|<span data-ttu-id="9845b-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="9845b-134">0x8004</span></span>|  
|<span data-ttu-id="9845b-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="9845b-135">SHA-256</span></span>|<span data-ttu-id="9845b-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="9845b-136">0x800c</span></span>|  
|<span data-ttu-id="9845b-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="9845b-137">SHA-384</span></span>|<span data-ttu-id="9845b-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="9845b-138">0x800d</span></span>|  
|<span data-ttu-id="9845b-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="9845b-139">SHA-512</span></span>|<span data-ttu-id="9845b-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="9845b-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9845b-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9845b-141">Requirements</span></span>  
 <span data-ttu-id="9845b-142">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9845b-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9845b-143">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="9845b-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="9845b-144">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9845b-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9845b-145">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9845b-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9845b-146">Confira também</span><span class="sxs-lookup"><span data-stu-id="9845b-146">See also</span></span>

- [<span data-ttu-id="9845b-147">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="9845b-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="9845b-148">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="9845b-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="9845b-149">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9845b-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="9845b-150">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="9845b-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
