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
ms.openlocfilehash: 8013d805716bbe6407eeed664966fe667282188a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135002"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="2b387-102">Método ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="2b387-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="2b387-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="2b387-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b387-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b387-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="2b387-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2b387-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="2b387-106">no O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="2b387-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="2b387-107">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="2b387-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="2b387-108">Se `pbKeyBlob` for NULL, `wszKeyContainer` deverá especificar um contêiner válido no CSP (provedor de serviços de criptografia).</span><span class="sxs-lookup"><span data-stu-id="2b387-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="2b387-109">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="2b387-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="2b387-110">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="2b387-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="2b387-111">As chaves devem ter chaves de assinatura de 1024 bits Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="2b387-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="2b387-112">Não há suporte para nenhum outro tipo de chave no momento.</span><span class="sxs-lookup"><span data-stu-id="2b387-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="2b387-113">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="2b387-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="2b387-114">Esse par está no formato criado pela função de `CryptExportKey` do Win32.</span><span class="sxs-lookup"><span data-stu-id="2b387-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="2b387-115">Se `pbKeyBlob` for NULL, o contêiner de chave especificado por `wszKeyContainer` será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="2b387-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="2b387-116">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2b387-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="2b387-117">fora Um ponteiro para o local no qual o Common Language Runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="2b387-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="2b387-118">Se `ppbSignatureBlob` for NULL, o tempo de execução armazenará a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="2b387-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="2b387-119">Se `ppbSignatureBlob` não for NULL, a Common Language Runtime alocará espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="2b387-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="2b387-120">O chamador deve liberar esse espaço usando o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2b387-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="2b387-121">fora O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="2b387-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b387-122">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2b387-122">Return Value</span></span>  
 <span data-ttu-id="2b387-123">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="2b387-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b387-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b387-124">Remarks</span></span>  
 <span data-ttu-id="2b387-125">Especifique NULL para `wszFilePath` calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="2b387-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="2b387-126">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="2b387-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b387-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b387-127">Requirements</span></span>  
 <span data-ttu-id="2b387-128">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b387-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b387-129">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="2b387-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="2b387-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2b387-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2b387-131">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b387-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b387-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b387-132">See also</span></span>

- [<span data-ttu-id="2b387-133">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="2b387-133">StrongNameSignatureGenerationEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="2b387-134">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2b387-134">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
