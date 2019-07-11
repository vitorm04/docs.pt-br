---
title: Função StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6e9e5c199ad437290d7bf19d65b5f29a0abed5e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780104"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="ab4ad-102">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="ab4ad-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="ab4ad-103">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="ab4ad-104">O par de chaves pode ser fornecido como um nome de contêiner de chave dentro de um provedor de serviços de criptografia (CSP) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="ab4ad-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-105">This function has been deprecated.</span></span> <span data-ttu-id="ab4ad-106">Use o [iclrstrongname:: Strongnamegetpublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab4ad-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ab4ad-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab4ad-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ab4ad-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="ab4ad-109">[in] O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="ab4ad-110">Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido dentro do CSP.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="ab4ad-111">Nesse caso, `StrongNameGetPublicKey` extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="ab4ad-112">Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="ab4ad-113">As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="ab4ad-114">Não há outros tipos de chaves têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="ab4ad-115">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="ab4ad-116">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="ab4ad-117">Se `pbKeyBlob` for nula, o contêiner de chave especificado por `szKeyContainer` deve para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="ab4ad-118">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="ab4ad-119">[out] A chave pública retornada BLOB.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="ab4ad-120">O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="ab4ad-121">O chamador deve liberar a memória usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="ab4ad-122">[out] O tamanho da chave pública retornado BLOB.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab4ad-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ab4ad-123">Return Value</span></span>  
 <span data-ttu-id="ab4ad-124">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab4ad-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="ab4ad-125">Remarks</span></span>  
 <span data-ttu-id="ab4ad-126">A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="ab4ad-127">Se o `StrongNameGetPublicKey` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="ab4ad-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab4ad-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ab4ad-128">Requirements</span></span>  
 <span data-ttu-id="ab4ad-129">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab4ad-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab4ad-130">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="ab4ad-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="ab4ad-131">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="ab4ad-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab4ad-132">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab4ad-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4ad-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ab4ad-133">See also</span></span>

- [<span data-ttu-id="ab4ad-134">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="ab4ad-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="ab4ad-135">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="ab4ad-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="ab4ad-136">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ab4ad-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="ab4ad-137">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="ab4ad-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
