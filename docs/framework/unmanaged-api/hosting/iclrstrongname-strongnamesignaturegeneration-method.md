---
title: Método ICLRStrongName::StrongNameSignatureGeneration
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178046"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="f610d-102">Método ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="f610d-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="f610d-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="f610d-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f610d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f610d-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f610d-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f610d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f610d-106">[em] O caminho para o arquivo que contém o manifesto da montagem para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="f610d-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="f610d-107">[em] O nome do recipiente de chave que contém o par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="f610d-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="f610d-108">Se `pbKeyBlob` for `wszKeyContainer` nulo, deve especificar um contêiner válido dentro do provedor de serviços criptográficos (CSP).</span><span class="sxs-lookup"><span data-stu-id="f610d-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="f610d-109">Neste caso, o par de chaves armazenado no recipiente é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="f610d-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="f610d-110">Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).</span><span class="sxs-lookup"><span data-stu-id="f610d-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="f610d-111">As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="f610d-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="f610d-112">Nenhum outro tipo de chaves é suportado neste momento.</span><span class="sxs-lookup"><span data-stu-id="f610d-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="f610d-113">[em] Um ponteiro para o par de tecla público/privado.</span><span class="sxs-lookup"><span data-stu-id="f610d-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="f610d-114">Este par está no formato criado pela `CryptExportKey` função Win32.</span><span class="sxs-lookup"><span data-stu-id="f610d-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="f610d-115">Se `pbKeyBlob` for nulo, o `wszKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="f610d-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="f610d-116">[em] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="f610d-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="f610d-117">[fora] Um ponteiro para o local para o qual o tempo de execução do idioma comum retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="f610d-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="f610d-118">Se `ppbSignatureBlob` for nulo, o tempo de execução `wszFilePath`armazena a assinatura no arquivo especificado por .</span><span class="sxs-lookup"><span data-stu-id="f610d-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="f610d-119">Se `ppbSignatureBlob` não for nulo, o tempo de execução do idioma comum aloca espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="f610d-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="f610d-120">O chamador deve liberar este espaço usando o método [ICLRStrongName::StrongNameFreeBuffer.](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)</span><span class="sxs-lookup"><span data-stu-id="f610d-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="f610d-121">[fora] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="f610d-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f610d-122">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f610d-122">Return Value</span></span>  
 <span data-ttu-id="f610d-123">`S_OK`se o método for concluído com sucesso; caso contrário, um valor HRESULT que indica falha (consulte [Valores comuns de HRESULT](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="f610d-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f610d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="f610d-124">Remarks</span></span>  
 <span data-ttu-id="f610d-125">Especifique nulo `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="f610d-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="f610d-126">A assinatura pode ser armazenada diretamente no arquivo ou devolvida ao chamador.</span><span class="sxs-lookup"><span data-stu-id="f610d-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f610d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f610d-127">Requirements</span></span>  
 <span data-ttu-id="f610d-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f610d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f610d-129">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="f610d-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f610d-130">**Biblioteca:** Incluído como um recurso em MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f610d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f610d-131">**.NET Framework Versions:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f610d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f610d-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="f610d-132">See also</span></span>

- [<span data-ttu-id="f610d-133">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="f610d-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="f610d-134">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f610d-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
