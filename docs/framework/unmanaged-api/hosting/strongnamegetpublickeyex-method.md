---
title: "Método StrongNameGetPublicKeyEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e94498cc8841a95e1918d3f26bd19256793564ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="aad61-102">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="aad61-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="aad61-103">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="aad61-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aad61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aad61-104">Syntax</span></span>  
  
```  
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
  
#### <a name="parameters"></a><span data-ttu-id="aad61-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aad61-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="aad61-106">[in] O nome do recipiente de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="aad61-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="aad61-107">Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP).</span><span class="sxs-lookup"><span data-stu-id="aad61-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="aad61-108">Nesse caso, o `StrongNameGetPublicKeyEx` método extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="aad61-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="aad61-109">Se `pbKeyBlob` não for null, o par de chaves é assumido para conter o objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="aad61-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="aad61-110">As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="aad61-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="aad61-111">Não há outros tipos de chaves têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="aad61-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="aad61-112">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="aad61-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="aad61-113">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="aad61-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="aad61-114">Se `pbKeyBlob` é null, o contêiner de chave especificado por `szKeyContainer` devem para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="aad61-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="aad61-115">[in] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="aad61-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="aad61-116">[out] A chave pública retornada BLOB.</span><span class="sxs-lookup"><span data-stu-id="aad61-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="aad61-117">O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="aad61-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="aad61-118">O chamador deve liberar a memória usando o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="aad61-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="aad61-119">[out] O tamanho da chave pública retornado BLOB.</span><span class="sxs-lookup"><span data-stu-id="aad61-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="aad61-120">[in] O algoritmo de hash do assembly.</span><span class="sxs-lookup"><span data-stu-id="aad61-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="aad61-121">Consulte a seção de comentários para obter uma lista de valores aceitos.</span><span class="sxs-lookup"><span data-stu-id="aad61-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="aad61-122">[in] Reservado para uso futuro; o padrão é nulo.</span><span class="sxs-lookup"><span data-stu-id="aad61-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aad61-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="aad61-123">Return Value</span></span>  
 <span data-ttu-id="aad61-124">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="aad61-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad61-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="aad61-125">Remarks</span></span>  
 <span data-ttu-id="aad61-126">A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="aad61-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aad61-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="aad61-127">Remarks</span></span>  
 <span data-ttu-id="aad61-128">A tabela a seguir mostra o conjunto de valores aceitos para o `uHashAlgId` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="aad61-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="aad61-129">Nome</span><span class="sxs-lookup"><span data-stu-id="aad61-129">Name</span></span>|<span data-ttu-id="aad61-130">Valor</span><span class="sxs-lookup"><span data-stu-id="aad61-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="aad61-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="aad61-131">None</span></span>|<span data-ttu-id="aad61-132">0</span><span class="sxs-lookup"><span data-stu-id="aad61-132">0</span></span>|  
|<span data-ttu-id="aad61-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="aad61-133">SHA-1</span></span>|<span data-ttu-id="aad61-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="aad61-134">0x8004</span></span>|  
|<span data-ttu-id="aad61-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="aad61-135">SHA-256</span></span>|<span data-ttu-id="aad61-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="aad61-136">0x800c</span></span>|  
|<span data-ttu-id="aad61-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="aad61-137">SHA-384</span></span>|<span data-ttu-id="aad61-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="aad61-138">0x800d</span></span>|  
|<span data-ttu-id="aad61-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="aad61-139">SHA-512</span></span>|<span data-ttu-id="aad61-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="aad61-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aad61-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aad61-141">Requirements</span></span>  
 <span data-ttu-id="aad61-142">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aad61-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aad61-143">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="aad61-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="aad61-144">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="aad61-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aad61-145">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aad61-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aad61-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aad61-146">See Also</span></span>  
 [<span data-ttu-id="aad61-147">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="aad61-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="aad61-148">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="aad61-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)  
 [<span data-ttu-id="aad61-149">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="aad61-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="aad61-150">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="aad61-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
