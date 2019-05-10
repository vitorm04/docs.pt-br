---
title: Função StrongNameSignatureGenerationEx
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059dadcaf7a55074e30c59873a8c1e7016b0a33e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64666003"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="b50e6-102">Função StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="b50e6-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="b50e6-103">Gera uma assinatura de nome forte para o assembly especificado, de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="b50e6-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="b50e6-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="b50e6-104">This function has been deprecated.</span></span> <span data-ttu-id="b50e6-105">Use o [iclrstrongname:: Strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b50e6-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b50e6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b50e6-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b50e6-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b50e6-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b50e6-108">[in] O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="b50e6-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b50e6-109">[in] O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b50e6-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b50e6-110">Se `pbKeyBlob` for nulo, `wszKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP).</span><span class="sxs-lookup"><span data-stu-id="b50e6-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b50e6-111">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="b50e6-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b50e6-112">Se `pbKeyBlob` não for nulo, presume-se o par de chaves para caber no objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="b50e6-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b50e6-113">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b50e6-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b50e6-114">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="b50e6-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b50e6-115">Se `pbKeyBlob` for nula, o contêiner de chave especificado por `wszKeyContainer` deve para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="b50e6-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b50e6-116">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="b50e6-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b50e6-117">[out] Um ponteiro para o local para o qual o common language runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b50e6-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b50e6-118">Se `ppbSignatureBlob` é nulo, o tempo de execução armazena a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="b50e6-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b50e6-119">Se `ppbSignatureBlob` é não nulo, o common language runtime aloca o espaço no qual retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b50e6-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b50e6-120">O chamador deve liberar esse espaço usando o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="b50e6-120">The caller must free this space using the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b50e6-121">[out] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="b50e6-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b50e6-122">[in] Um ou mais dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b50e6-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="b50e6-123">`SN_SIGN_ALL_FILES` (0x00000001) - recalcular os hashes de todos os módulos vinculado.</span><span class="sxs-lookup"><span data-stu-id="b50e6-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="b50e6-124">`SN_TEST_SIGN` (0x00000002) - teste-assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="b50e6-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b50e6-125">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b50e6-125">Return Value</span></span>  
 <span data-ttu-id="b50e6-126">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b50e6-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b50e6-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b50e6-127">Remarks</span></span>  
 <span data-ttu-id="b50e6-128">Especifique null para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b50e6-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b50e6-129">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="b50e6-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="b50e6-130">Se `SN_SIGN_ALL_FILES` for especificado, mas uma chave pública não está incluída (ambos `pbKeyBlob` e `wszFilePath` são nulos), os hashes para módulos vinculados são recalculados, mas o assembly não está assinado novamente.</span><span class="sxs-lookup"><span data-stu-id="b50e6-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="b50e6-131">Se `SN_TEST_SIGN` for especificado, o cabeçalho do common language runtime não é modificado para indicar que o assembly é assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b50e6-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="b50e6-132">Se o `StrongNameSignatureGenerationEx` função não for concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="b50e6-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b50e6-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b50e6-133">Requirements</span></span>  
 <span data-ttu-id="b50e6-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b50e6-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b50e6-135">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b50e6-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b50e6-136">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="b50e6-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b50e6-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b50e6-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b50e6-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b50e6-138">See also</span></span>

- [<span data-ttu-id="b50e6-139">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="b50e6-139">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="b50e6-140">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="b50e6-140">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="b50e6-141">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b50e6-141">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
