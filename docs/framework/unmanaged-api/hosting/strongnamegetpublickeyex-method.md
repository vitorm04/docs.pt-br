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
ms.openlocfilehash: 700bcc5b818c452d3642d325fb6fe19cbb162474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141449"
---
# <a name="strongnamegetpublickeyex-method"></a><span data-ttu-id="8eb1e-102">Método StrongNameGetPublicKeyEx</span><span class="sxs-lookup"><span data-stu-id="8eb1e-102">StrongNameGetPublicKeyEx Method</span></span>
<span data-ttu-id="8eb1e-103">Obtém a chave pública de um par de chaves pública/privada e especifica um algoritmo de hash e um algoritmo de assinatura.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-103">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eb1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8eb1e-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8eb1e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8eb1e-105">Parameters</span></span>  
 `pwzKeyContainer`  
 <span data-ttu-id="8eb1e-106">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-106">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="8eb1e-107">Se `pbKeyBlob` for NULL, `szKeyContainer` deverá especificar um contêiner válido no CSP (provedor de serviços de criptografia).</span><span class="sxs-lookup"><span data-stu-id="8eb1e-107">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="8eb1e-108">Nesse caso, o método `StrongNameGetPublicKeyEx` extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-108">In this case, the `StrongNameGetPublicKeyEx` method extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="8eb1e-109">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-109">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="8eb1e-110">As chaves devem ter chaves de assinatura de 1024 bits Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="8eb1e-110">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="8eb1e-111">Não há suporte para nenhum outro tipo de chave no momento.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-111">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="8eb1e-112">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-112">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="8eb1e-113">Esse par está no formato criado pela função de `CryptExportKey` do Win32.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-113">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="8eb1e-114">Se `pbKeyBlob` for NULL, o contêiner de chave especificado por `szKeyContainer` será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-114">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="8eb1e-115">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-115">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="8eb1e-116">fora O BLOB de chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-116">[out] The returned public key BLOB.</span></span> <span data-ttu-id="8eb1e-117">O parâmetro `ppbPublicKeyBlob` é alocado pelo Common Language Runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-117">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="8eb1e-118">O chamador deve liberar a memória usando o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8eb1e-118">The caller must free the memory by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="8eb1e-119">fora O tamanho do BLOB de chave pública retornado.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-119">[out] The size of the returned public key BLOB.</span></span>  
  
 `uHashAlgId`  
 <span data-ttu-id="8eb1e-120">no O algoritmo de hash de assembly.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-120">[in] The assembly hash algorithm.</span></span> <span data-ttu-id="8eb1e-121">Consulte a seção comentários para obter uma lista de valores aceitos.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-121">See the Remarks section for a list of accepted values.</span></span>  
  
 `uReserved`  
 <span data-ttu-id="8eb1e-122">no Reservado para uso futuro; o padrão é NULL.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-122">[in] Reserved for future use; defaults to null.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8eb1e-123">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8eb1e-123">Return Value</span></span>  
 <span data-ttu-id="8eb1e-124">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="8eb1e-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eb1e-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eb1e-125">Remarks</span></span>  
 <span data-ttu-id="8eb1e-126">A chave pública está contida em uma estrutura [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="8eb1e-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eb1e-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="8eb1e-127">Remarks</span></span>  
 <span data-ttu-id="8eb1e-128">A tabela a seguir mostra o conjunto de valores aceitos para o parâmetro `uHashAlgId`.</span><span class="sxs-lookup"><span data-stu-id="8eb1e-128">The following table shows the set of accepted values for the `uHashAlgId` parameter.</span></span>  
  
|<span data-ttu-id="8eb1e-129">Name</span><span class="sxs-lookup"><span data-stu-id="8eb1e-129">Name</span></span>|<span data-ttu-id="8eb1e-130">Valor</span><span class="sxs-lookup"><span data-stu-id="8eb1e-130">Value</span></span>|  
|----------|-----------|  
|<span data-ttu-id="8eb1e-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8eb1e-131">None</span></span>|<span data-ttu-id="8eb1e-132">0</span><span class="sxs-lookup"><span data-stu-id="8eb1e-132">0</span></span>|  
|<span data-ttu-id="8eb1e-133">SHA-1</span><span class="sxs-lookup"><span data-stu-id="8eb1e-133">SHA-1</span></span>|<span data-ttu-id="8eb1e-134">0x8004</span><span class="sxs-lookup"><span data-stu-id="8eb1e-134">0x8004</span></span>|  
|<span data-ttu-id="8eb1e-135">SHA-256</span><span class="sxs-lookup"><span data-stu-id="8eb1e-135">SHA-256</span></span>|<span data-ttu-id="8eb1e-136">0x800c</span><span class="sxs-lookup"><span data-stu-id="8eb1e-136">0x800c</span></span>|  
|<span data-ttu-id="8eb1e-137">SHA-384</span><span class="sxs-lookup"><span data-stu-id="8eb1e-137">SHA-384</span></span>|<span data-ttu-id="8eb1e-138">0x800d</span><span class="sxs-lookup"><span data-stu-id="8eb1e-138">0x800d</span></span>|  
|<span data-ttu-id="8eb1e-139">SHA-512</span><span class="sxs-lookup"><span data-stu-id="8eb1e-139">SHA-512</span></span>|<span data-ttu-id="8eb1e-140">0x800e</span><span class="sxs-lookup"><span data-stu-id="8eb1e-140">0x800e</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8eb1e-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8eb1e-141">Requirements</span></span>  
 <span data-ttu-id="8eb1e-142">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eb1e-142">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eb1e-143">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="8eb1e-143">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="8eb1e-144">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8eb1e-144">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8eb1e-145">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eb1e-145">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eb1e-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8eb1e-146">See also</span></span>

- [<span data-ttu-id="8eb1e-147">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="8eb1e-147">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="8eb1e-148">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="8eb1e-148">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [<span data-ttu-id="8eb1e-149">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="8eb1e-149">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="8eb1e-150">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="8eb1e-150">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
