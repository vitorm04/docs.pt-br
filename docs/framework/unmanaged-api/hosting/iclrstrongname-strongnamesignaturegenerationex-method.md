---
title: "Método ICLRStrongName::StrongNameSignatureGenerationEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGenerationEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 247bcfa3c9f7a02dea331ff14948a00812fb06e5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="78f80-102">Método ICLRStrongName::StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="78f80-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="78f80-103">Gera uma assinatura de nome forte para o assembly especificado, de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="78f80-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78f80-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78f80-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="78f80-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78f80-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="78f80-106">[in] O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="78f80-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="78f80-107">[in] O nome do recipiente de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="78f80-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="78f80-108">Se `pbKeyBlob` for nulo, `wszKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP).</span><span class="sxs-lookup"><span data-stu-id="78f80-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="78f80-109">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="78f80-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="78f80-110">Se `pbKeyBlob` não for null, o par de chaves é assumido para conter o objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="78f80-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="78f80-111">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="78f80-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="78f80-112">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="78f80-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="78f80-113">Se `pbKeyBlob` é null, o contêiner de chave especificado por `wszKeyContainer` devem para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="78f80-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="78f80-114">[in] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="78f80-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="78f80-115">[out] Um ponteiro para o local para o qual o common language runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="78f80-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="78f80-116">Se `ppbSignatureBlob` é null, o tempo de execução armazena a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="78f80-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="78f80-117">Se `ppbSignatureBlob` é não nulo, o common language runtime aloca espaço no qual retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="78f80-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="78f80-118">O chamador deve liberar esse espaço usando o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="78f80-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="78f80-119">[out] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="78f80-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="78f80-120">[in] Um ou mais dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="78f80-120">[in] One or more of the following values:</span></span>  
  
-   <span data-ttu-id="78f80-121">`SN_SIGN_ALL_FILES`(0x00000001) - recompilar todos os hashes de módulos vinculados.</span><span class="sxs-lookup"><span data-stu-id="78f80-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
-   <span data-ttu-id="78f80-122">`SN_TEST_SIGN`(0x00000002) - teste-assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="78f80-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78f80-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="78f80-123">Return Value</span></span>  
 <span data-ttu-id="78f80-124">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="78f80-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78f80-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="78f80-125">Remarks</span></span>  
 <span data-ttu-id="78f80-126">Especifique null para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="78f80-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="78f80-127">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="78f80-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="78f80-128">Se `SN_SIGN_ALL_FILES` for especificado, mas não há uma chave pública (ambos `pbKeyBlob` e `wszFilePath` são nulos), hashes de módulos vinculados são recalculados, mas o assembly não está assinado novamente.</span><span class="sxs-lookup"><span data-stu-id="78f80-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="78f80-129">Se `SN_TEST_SIGN` for especificado, o cabeçalho de tempo de execução de linguagem comum não é modificado para indicar que o assembly é assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="78f80-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78f80-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78f80-130">Requirements</span></span>  
 <span data-ttu-id="78f80-131">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78f80-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78f80-132">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="78f80-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="78f80-133">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="78f80-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="78f80-134">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78f80-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78f80-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78f80-135">See Also</span></span>  
 [<span data-ttu-id="78f80-136">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="78f80-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)  
 [<span data-ttu-id="78f80-137">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="78f80-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
