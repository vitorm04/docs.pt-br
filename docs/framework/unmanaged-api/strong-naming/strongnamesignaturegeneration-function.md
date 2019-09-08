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
ms.openlocfilehash: 48cdd550e5d8c7c75a603d74456e99a066d5c599
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798972"
---
# <a name="strongnamesignaturegeneration-function"></a><span data-ttu-id="28ffb-102">Função StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="28ffb-102">StrongNameSignatureGeneration Function</span></span>
<span data-ttu-id="28ffb-103">Gera uma assinatura de nome forte para o assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="28ffb-103">Generates a strong name signature for the specified assembly.</span></span>  
  
 <span data-ttu-id="28ffb-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="28ffb-104">This function has been deprecated.</span></span> <span data-ttu-id="28ffb-105">Em vez disso, use o método [ICLRStrongName:: StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) .</span><span class="sxs-lookup"><span data-stu-id="28ffb-105">Use the [ICLRStrongName::StrongNameSignatureGeneration](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28ffb-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="28ffb-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="28ffb-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="28ffb-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="28ffb-108">no O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="28ffb-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="28ffb-109">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="28ffb-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="28ffb-110">Se `pbKeyBlob` for NULL, `wszKeyContainer` deve especificar um contêiner válido no CSP (provedor de serviços de criptografia).</span><span class="sxs-lookup"><span data-stu-id="28ffb-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="28ffb-111">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="28ffb-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="28ffb-112">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="28ffb-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="28ffb-113">As chaves devem ter chaves de assinatura de 1024 bits Rivest-Shamir-Adleman (RSA).</span><span class="sxs-lookup"><span data-stu-id="28ffb-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="28ffb-114">Não há suporte para nenhum outro tipo de chave no momento.</span><span class="sxs-lookup"><span data-stu-id="28ffb-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="28ffb-115">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="28ffb-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="28ffb-116">Esse par está no formato criado pela função do Win32 `CryptExportKey` .</span><span class="sxs-lookup"><span data-stu-id="28ffb-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="28ffb-117">Se `pbKeyBlob` for NULL, o contêiner de chave especificado `wszKeyContainer` por será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="28ffb-117">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="28ffb-118">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="28ffb-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="28ffb-119">fora Um ponteiro para o local no qual o Common Language Runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="28ffb-119">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="28ffb-120">Se `ppbSignatureBlob` for NULL, o tempo de execução armazenará a assinatura no arquivo `wszFilePath`especificado por.</span><span class="sxs-lookup"><span data-stu-id="28ffb-120">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="28ffb-121">Se `ppbSignatureBlob` não for NULL, o common language runtime aloca espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="28ffb-121">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="28ffb-122">O chamador deve liberar esse espaço usando a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="28ffb-122">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="28ffb-123">fora O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="28ffb-123">[out] The size, in bytes, of the returned signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28ffb-124">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="28ffb-124">Return Value</span></span>  
 <span data-ttu-id="28ffb-125">`true`após a conclusão bem-sucedida; caso contrário `false`,.</span><span class="sxs-lookup"><span data-stu-id="28ffb-125">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28ffb-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="28ffb-126">Remarks</span></span>  
 <span data-ttu-id="28ffb-127">Especifique NULL para `wszFilePath` para calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="28ffb-127">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="28ffb-128">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="28ffb-128">The signature can be stored either directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="28ffb-129">Se a `StrongNameSignatureGeneration` função não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="28ffb-129">If the `StrongNameSignatureGeneration` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28ffb-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="28ffb-130">Requirements</span></span>  
 <span data-ttu-id="28ffb-131">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28ffb-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28ffb-132">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="28ffb-132">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="28ffb-133">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="28ffb-133">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="28ffb-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28ffb-134">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28ffb-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28ffb-135">See also</span></span>

- [<span data-ttu-id="28ffb-136">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="28ffb-136">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="28ffb-137">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="28ffb-137">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="28ffb-138">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="28ffb-138">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
