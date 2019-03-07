---
title: Função StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55ff59d698a1ced689e23d9908ce6e273d8a9c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494539"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="955e2-102">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="955e2-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="955e2-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="955e2-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="955e2-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="955e2-104">This function has been deprecated.</span></span> <span data-ttu-id="955e2-105">Use o [iclrstrongname:: Strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="955e2-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955e2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="955e2-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="955e2-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="955e2-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="955e2-108">[in] O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="955e2-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="955e2-109">[in] O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="955e2-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="955e2-110">Se `pbKeyBlob` for nulo, `wszKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP).</span><span class="sxs-lookup"><span data-stu-id="955e2-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="955e2-111">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="955e2-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="955e2-112">Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="955e2-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="955e2-113">As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="955e2-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="955e2-114">Não há outros tipos de chaves têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="955e2-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="955e2-115">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="955e2-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="955e2-116">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="955e2-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="955e2-117">Se `pbKeyBlob` for nula, o contêiner de chave especificado por `wszKeyContainer` deve para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="955e2-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="955e2-118">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="955e2-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="955e2-119">[out] Um ponteiro para o local para o qual o common language runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="955e2-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="955e2-120">Se `ppbSignatureBlob` é nulo, o tempo de execução armazena a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="955e2-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="955e2-121">Se `ppbSignatureBlob` é não nulo, o common language runtime aloca o espaço no qual retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="955e2-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="955e2-122">O chamador deve liberar esse espaço usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="955e2-122">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="955e2-123">[out] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="955e2-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="955e2-124">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="955e2-124">Return Value</span></span>  
 <span data-ttu-id="955e2-125">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="955e2-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="955e2-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="955e2-126">Remarks</span></span>  
 <span data-ttu-id="955e2-127">Especifique null para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="955e2-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="955e2-128">A assinatura pode ser armazenados diretamente no arquivo ou retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="955e2-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="955e2-129">Se o `StrongNameSignatureGeneration` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="955e2-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="955e2-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="955e2-130">Requirements</span></span>  
 <span data-ttu-id="955e2-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="955e2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="955e2-132">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="955e2-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="955e2-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="955e2-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="955e2-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="955e2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="955e2-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="955e2-135">See also</span></span>
- [<span data-ttu-id="955e2-136">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="955e2-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="955e2-137">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="955e2-137">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="955e2-138">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="955e2-138">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
