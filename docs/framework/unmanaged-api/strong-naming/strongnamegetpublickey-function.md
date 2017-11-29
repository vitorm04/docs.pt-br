---
title: "Função StrongNameGetPublicKey"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type: DLLExport
f1_keywords: StrongNameGetPublicKey
helpviewer_keywords: StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 243b5f8d94805d8631c7c79f424d9e6434213bb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="c6734-102">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="c6734-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="c6734-103">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="c6734-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="c6734-104">O par de chaves pode ser fornecido como um nome de contêiner de chave em um provedor de serviços de criptografia (CSP) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="c6734-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="c6734-105">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="c6734-105">This function has been deprecated.</span></span> <span data-ttu-id="c6734-106">Use o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c6734-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6734-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6734-107">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6734-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6734-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="c6734-109">[in] O nome do recipiente de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="c6734-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="c6734-110">Se `pbKeyBlob` for nulo, `szKeyContainer` deve especificar um contêiner válido dentro do CSP.</span><span class="sxs-lookup"><span data-stu-id="c6734-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="c6734-111">Nesse caso, `StrongNameGetPublicKey` extrai a chave pública do par de chaves armazenado no contêiner.</span><span class="sxs-lookup"><span data-stu-id="c6734-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="c6734-112">Se `pbKeyBlob` não for null, o par de chaves é assumido para conter o objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="c6734-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="c6734-113">As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="c6734-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="c6734-114">Não há outros tipos de chaves têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="c6734-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="c6734-115">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="c6734-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="c6734-116">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="c6734-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="c6734-117">Se `pbKeyBlob` é null, o contêiner de chave especificado por `szKeyContainer` devem para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="c6734-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="c6734-118">[in] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="c6734-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="c6734-119">[out] A chave pública retornada BLOB.</span><span class="sxs-lookup"><span data-stu-id="c6734-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="c6734-120">O `ppbPublicKeyBlob` parâmetro é alocado pelo common language runtime e retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="c6734-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="c6734-121">O chamador deve liberar a memória usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="c6734-121">The caller must free the memory by using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="c6734-122">[out] O tamanho da chave pública retornado BLOB.</span><span class="sxs-lookup"><span data-stu-id="c6734-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6734-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c6734-123">Return Value</span></span>  
 <span data-ttu-id="c6734-124">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="c6734-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6734-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6734-125">Remarks</span></span>  
 <span data-ttu-id="c6734-126">A chave pública está contida em uma [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) estrutura.</span><span class="sxs-lookup"><span data-stu-id="c6734-126">The public key is contained in a [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="c6734-127">Se o `StrongNameGetPublicKey` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="c6734-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6734-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6734-128">Requirements</span></span>  
 <span data-ttu-id="c6734-129">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6734-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6734-130">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="c6734-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="c6734-131">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="c6734-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c6734-132">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6734-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6734-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6734-133">See Also</span></span>  
 [<span data-ttu-id="c6734-134">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="c6734-134">StrongNameGetPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)  
 [<span data-ttu-id="c6734-135">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="c6734-135">StrongNameTokenFromPublicKey Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)  
 [<span data-ttu-id="c6734-136">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c6734-136">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 [<span data-ttu-id="c6734-137">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="c6734-137">PublicKeyBlob Structure</span></span>](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
