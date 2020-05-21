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
ms.openlocfilehash: a8c9eab719f6a4f233490e544f67cf779ea10b20
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763027"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a><span data-ttu-id="1232d-102">Método ICLRStrongName::StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="1232d-102">ICLRStrongName::StrongNameSignatureGeneration Method</span></span>
<span data-ttu-id="1232d-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="1232d-103">Generates a strong name signature for the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1232d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1232d-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="1232d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1232d-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="1232d-106">no O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="1232d-106">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="1232d-107">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="1232d-107">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="1232d-108">Se `pbKeyBlob` for NULL, `wszKeyContainer` deve especificar um contêiner válido no CSP (provedor de serviços de criptografia).</span><span class="sxs-lookup"><span data-stu-id="1232d-108">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="1232d-109">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="1232d-109">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="1232d-110">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="1232d-110">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="1232d-111">As chaves devem ter chaves de assinatura de 1024 bits Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="1232d-111">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="1232d-112">Não há suporte para nenhum outro tipo de chave no momento.</span><span class="sxs-lookup"><span data-stu-id="1232d-112">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="1232d-113">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="1232d-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="1232d-114">Esse par está no formato criado pela função do Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="1232d-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="1232d-115">Se `pbKeyBlob` for NULL, o contêiner de chave especificado por `wszKeyContainer` será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="1232d-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="1232d-116">no O tamanho, em bytes, de `pbKeyBlob` .</span><span class="sxs-lookup"><span data-stu-id="1232d-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="1232d-117">fora Um ponteiro para o local no qual o Common Language Runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="1232d-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="1232d-118">Se `ppbSignatureBlob` for NULL, o tempo de execução armazenará a assinatura no arquivo especificado por `wszFilePath` .</span><span class="sxs-lookup"><span data-stu-id="1232d-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="1232d-119">Se `ppbSignatureBlob` não for NULL, o common language runtime aloca espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="1232d-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="1232d-120">O chamador deve liberar esse espaço usando o método [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1232d-120">The caller must free this space by using the [ICLRStrongName::StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md) method.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="1232d-121">fora O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="1232d-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1232d-122">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="1232d-122">Return Value</span></span>  
 <span data-ttu-id="1232d-123">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="1232d-123">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1232d-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="1232d-124">Remarks</span></span>  
 <span data-ttu-id="1232d-125">Especifique NULL para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="1232d-125">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="1232d-126">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="1232d-126">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1232d-127">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1232d-127">Requirements</span></span>  
 <span data-ttu-id="1232d-128">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1232d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1232d-129">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="1232d-129">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="1232d-130">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1232d-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1232d-131">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1232d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1232d-132">Veja também</span><span class="sxs-lookup"><span data-stu-id="1232d-132">See also</span></span>

- [<span data-ttu-id="1232d-133">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="1232d-133">StrongNameSignatureGenerationEx Method</span></span>](iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="1232d-134">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="1232d-134">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
