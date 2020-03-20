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
ms.openlocfilehash: d7f481e5c61ec65d2e7414bd47227866f3435028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176897"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="81131-102">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="81131-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="81131-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="81131-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="81131-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="81131-104">This function has been deprecated.</span></span> <span data-ttu-id="81131-105">Use o método [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="81131-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81131-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="81131-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81131-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="81131-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="81131-108">[em] O caminho para o arquivo que contém o manifesto da montagem para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="81131-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="81131-109">[em] O nome do recipiente de chave que contém o par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="81131-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="81131-110">Se `pbKeyBlob` for `wszKeyContainer` nulo, deve especificar um contêiner válido dentro do provedor de serviços criptográficos (CSP).</span><span class="sxs-lookup"><span data-stu-id="81131-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="81131-111">Neste caso, o par de chaves armazenado no recipiente é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="81131-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="81131-112">Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).</span><span class="sxs-lookup"><span data-stu-id="81131-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="81131-113">As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="81131-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="81131-114">Nenhum outro tipo de chaves é suportado neste momento.</span><span class="sxs-lookup"><span data-stu-id="81131-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="81131-115">[em] Um ponteiro para o par de tecla público/privado.</span><span class="sxs-lookup"><span data-stu-id="81131-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="81131-116">Este par está no formato criado pela `CryptExportKey` função Win32.</span><span class="sxs-lookup"><span data-stu-id="81131-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="81131-117">Se `pbKeyBlob` for nulo, o `wszKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="81131-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="81131-118">[em] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="81131-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="81131-119">[fora] Um ponteiro para o local para o qual o tempo de execução do idioma comum retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="81131-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="81131-120">Se `ppbSignatureBlob` for nulo, o tempo de execução `wszFilePath`armazena a assinatura no arquivo especificado por .</span><span class="sxs-lookup"><span data-stu-id="81131-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="81131-121">Se `ppbSignatureBlob` não for nulo, o tempo de execução do idioma comum aloca espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="81131-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="81131-122">O chamador deve liberar este espaço usando a função [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="81131-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="81131-123">[fora] O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="81131-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81131-124">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="81131-124">Return Value</span></span>  
 <span data-ttu-id="81131-125">`true`em conclusão bem sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="81131-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81131-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="81131-126">Remarks</span></span>  
 <span data-ttu-id="81131-127">Especifique nulo `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="81131-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="81131-128">A assinatura pode ser armazenada diretamente no arquivo ou devolvida ao chamador.</span><span class="sxs-lookup"><span data-stu-id="81131-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="81131-129">Se `StrongNameSignatureGeneration` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="81131-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81131-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="81131-130">Requirements</span></span>  
 <span data-ttu-id="81131-131">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81131-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81131-132">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="81131-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="81131-133">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="81131-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="81131-134">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81131-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81131-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="81131-135">See also</span></span>

- [<span data-ttu-id="81131-136">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="81131-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="81131-137">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="81131-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="81131-138">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="81131-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
