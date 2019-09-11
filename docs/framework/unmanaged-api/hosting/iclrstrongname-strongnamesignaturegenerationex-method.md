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
ms.openlocfilehash: b411a51a5640a924d3eeae5d52102a842966d3fa
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855502"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a><span data-ttu-id="b7713-102">Método ICLRStrongName::StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="b7713-102">ICLRStrongName::StrongNameSignatureGenerationEx Method</span></span>
<span data-ttu-id="b7713-103">Gera uma assinatura de nome forte para o assembly especificado, de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="b7713-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7713-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7713-104">Syntax</span></span>  
  
```cpp
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
  
## <a name="parameters"></a><span data-ttu-id="b7713-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b7713-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b7713-106">no O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="b7713-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b7713-107">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b7713-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b7713-108">Se `pbKeyBlob` for NULL, `wszKeyContainer` deve especificar um contêiner válido no CSP (provedor de serviços de criptografia).</span><span class="sxs-lookup"><span data-stu-id="b7713-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b7713-109">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="b7713-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b7713-110">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="b7713-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b7713-111">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b7713-111">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b7713-112">Esse par está no formato criado pela função do Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="b7713-112">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b7713-113">Se `pbKeyBlob` for NULL, o contêiner de chave especificado `wszKeyContainer` por será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="b7713-113">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b7713-114">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="b7713-114">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b7713-115">fora Um ponteiro para o local no qual o Common Language Runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b7713-115">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b7713-116">Se `ppbSignatureBlob` for NULL, o tempo de execução armazenará a assinatura no arquivo `wszFilePath`especificado por.</span><span class="sxs-lookup"><span data-stu-id="b7713-116">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b7713-117">Se `ppbSignatureBlob` não for NULL, o common language runtime aloca espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b7713-117">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b7713-118">O chamador deve liberar esse espaço usando o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b7713-118">The caller must free this space using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b7713-119">fora O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="b7713-119">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b7713-120">no Um ou mais dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b7713-120">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="b7713-121">`SN_SIGN_ALL_FILES`(0x00000001) – recomputar todos os hashes para módulos vinculados.</span><span class="sxs-lookup"><span data-stu-id="b7713-121">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="b7713-122">`SN_TEST_SIGN`(0x00000002)-testar o assembly.</span><span class="sxs-lookup"><span data-stu-id="b7713-122">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b7713-123">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b7713-123">Return Value</span></span>  
 <span data-ttu-id="b7713-124">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="b7713-124">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b7713-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="b7713-125">Remarks</span></span>  
 <span data-ttu-id="b7713-126">Especifique NULL para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b7713-126">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b7713-127">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="b7713-127">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="b7713-128">Se `SN_SIGN_ALL_FILES` for especificado, mas uma chave pública não estiver incluída `pbKeyBlob` (e `wszFilePath` forem nulas), os hashes para módulos vinculados serão recalculados, mas o assembly não será assinado novamente.</span><span class="sxs-lookup"><span data-stu-id="b7713-128">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="b7713-129">Se `SN_TEST_SIGN` for especificado, o cabeçalho de Common Language Runtime não será modificado para indicar que o assembly é assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b7713-129">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7713-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b7713-130">Requirements</span></span>  
 <span data-ttu-id="b7713-131">**Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7713-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7713-132">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="b7713-132">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="b7713-133">**Biblioteca** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b7713-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b7713-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7713-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7713-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7713-135">See also</span></span>

- [<span data-ttu-id="b7713-136">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="b7713-136">StrongNameSignatureGeneration Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="b7713-137">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b7713-137">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
