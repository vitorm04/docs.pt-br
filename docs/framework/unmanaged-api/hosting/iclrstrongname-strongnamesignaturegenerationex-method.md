---
title: Método ICLRStrongName::StrongNameSignatureGenerationEx
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81f1eb4236bab72caf4421342e1f54d6d2f32607
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078334"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="75ddb-102">Método ICLRStrongName::StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="75ddb-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="75ddb-103">Gera uma assinatura de nome forte para o assembly especificado, de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="75ddb-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75ddb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75ddb-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="75ddb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75ddb-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="75ddb-106">[in] O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="75ddb-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="75ddb-107">[in] O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="75ddb-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="75ddb-108">Se `pbKeyBlob` for nulo, `wszKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP).</span><span class="sxs-lookup"><span data-stu-id="75ddb-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="75ddb-109">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="75ddb-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="75ddb-110">Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="75ddb-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="75ddb-111">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="75ddb-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="75ddb-112">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="75ddb-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="75ddb-113">Se `pbKeyBlob` for nula, o contêiner de chave especificado por `wszKeyContainer` deve para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="75ddb-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="75ddb-114">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="75ddb-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="75ddb-115">[out] Um ponteiro para o local para o qual o common language runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="75ddb-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="75ddb-116">Se `ppbSignatureBlob` é nulo, o tempo de execução armazena a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="75ddb-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="75ddb-117">Se `ppbSignatureBlob` é não nulo, o common language runtime aloca o espaço no qual retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="75ddb-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="75ddb-118">O chamador deve liberar esse espaço usando o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="75ddb-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="75ddb-119">[out] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="75ddb-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="75ddb-120">[in] Um ou mais dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="75ddb-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="75ddb-121">`SN_SIGN_ALL_FILES` (0x00000001) - recalcular os hashes de todos os módulos vinculado.</span><span class="sxs-lookup"><span data-stu-id="75ddb-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="75ddb-122">`SN_TEST_SIGN` (0x00000002) - teste-assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="75ddb-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75ddb-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="75ddb-123">Return Value</span></span>  
 <span data-ttu-id="75ddb-124">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="75ddb-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75ddb-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="75ddb-125">Remarks</span></span>  
 <span data-ttu-id="75ddb-126">Especifique null para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="75ddb-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="75ddb-127">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="75ddb-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="75ddb-128">Se `SN_SIGN_ALL_FILES` for especificado, mas uma chave pública não está incluída (ambos `pbKeyBlob` e `wszFilePath` são nulos), os hashes para módulos vinculados são recalculados, mas o assembly não está assinado novamente.</span><span class="sxs-lookup"><span data-stu-id="75ddb-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="75ddb-129">Se `SN_TEST_SIGN` for especificado, o cabeçalho do common language runtime não é modificado para indicar que o assembly é assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="75ddb-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75ddb-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75ddb-130">Requirements</span></span>  
 <span data-ttu-id="75ddb-131">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75ddb-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75ddb-132">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="75ddb-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="75ddb-133">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="75ddb-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="75ddb-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75ddb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75ddb-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75ddb-135">See Also</span></span>  
 [<span data-ttu-id="75ddb-136">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="75ddb-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="75ddb-137">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="75ddb-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
