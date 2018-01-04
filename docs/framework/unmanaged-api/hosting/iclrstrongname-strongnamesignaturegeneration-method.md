---
title: "Método ICLRStrongName::StrongNameSignatureGeneration"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameSignatureGeneration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fcf872dcd1de34aaade06cf26914a75ae971b85b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="0c76d-102">Método ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="0c76d-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="0c76d-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="0c76d-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c76d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0c76d-104">Syntax</span></span>  
  
```  
HRESULT StrongNameSignatureGeneration (   
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c76d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0c76d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="0c76d-106">[in] O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="0c76d-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="0c76d-107">[in] O nome do recipiente de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="0c76d-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="0c76d-108">Se `pbKeyBlob` for nulo, `wszKeyContainer` deve especificar um contêiner válido no provedor de serviços de criptografia (CSP).</span><span class="sxs-lookup"><span data-stu-id="0c76d-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="0c76d-109">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="0c76d-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="0c76d-110">Se `pbKeyBlob` não for null, o par de chaves é assumido para conter o objeto binário grande (BLOB) chave.</span><span class="sxs-lookup"><span data-stu-id="0c76d-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="0c76d-111">As chaves devem ser Rivest-Shamir-Adleman (RSA de 1024 bits) chaves de assinatura.</span><span class="sxs-lookup"><span data-stu-id="0c76d-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="0c76d-112">Não há outros tipos de chaves têm suporte no momento.</span><span class="sxs-lookup"><span data-stu-id="0c76d-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="0c76d-113">[in] Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="0c76d-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="0c76d-114">Esse par está no formato criado pelo Win32 `CryptExportKey` função.</span><span class="sxs-lookup"><span data-stu-id="0c76d-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="0c76d-115">Se `pbKeyBlob` é null, o contêiner de chave especificado por `wszKeyContainer` devem para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="0c76d-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="0c76d-116">[in] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="0c76d-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="0c76d-117">[out] Um ponteiro para o local para o qual o common language runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="0c76d-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="0c76d-118">Se `ppbSignatureBlob` é null, o tempo de execução armazena a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="0c76d-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="0c76d-119">Se `ppbSignatureBlob` é não nulo, o common language runtime aloca espaço no qual retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="0c76d-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="0c76d-120">O chamador deve esse espaço livre usando o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0c76d-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="0c76d-121">[out] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="0c76d-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c76d-122">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0c76d-122">Return Value</span></span>  
 <span data-ttu-id="0c76d-123">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="0c76d-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c76d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="0c76d-124">Remarks</span></span>  
 <span data-ttu-id="0c76d-125">Especifique null para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="0c76d-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="0c76d-126">A assinatura pode ser armazenados diretamente no arquivo ou retornado ao chamador.</span><span class="sxs-lookup"><span data-stu-id="0c76d-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c76d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0c76d-127">Requirements</span></span>  
 <span data-ttu-id="0c76d-128">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c76d-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c76d-129">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="0c76d-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="0c76d-130">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="0c76d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c76d-131">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c76d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c76d-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0c76d-132">See Also</span></span>  
 [<span data-ttu-id="0c76d-133">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="0c76d-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)  
 [<span data-ttu-id="0c76d-134">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="0c76d-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
