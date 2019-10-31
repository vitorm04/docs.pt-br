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
ms.openlocfilehash: e8f63a6379af8f2b7b88c511840622d49d65d587
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141580"
---
# <a name="strongnamesignaturegenerationex-function"></a><span data-ttu-id="b3049-102">Função StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="b3049-102">StrongNameSignatureGenerationEx Function</span></span>
<span data-ttu-id="b3049-103">Gera uma assinatura de nome forte para o assembly especificado, de acordo com os sinalizadores especificados.</span><span class="sxs-lookup"><span data-stu-id="b3049-103">Generates a strong name signature for the specified assembly, according to the specified flags.</span></span>  
  
 <span data-ttu-id="b3049-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="b3049-104">This function has been deprecated.</span></span> <span data-ttu-id="b3049-105">Em vez disso, use o método [ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b3049-105">Use the [ICLRStrongName::StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3049-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3049-106">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="b3049-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3049-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="b3049-108">no O caminho para o arquivo que contém o manifesto do assembly para o qual a assinatura de nome forte será gerada.</span><span class="sxs-lookup"><span data-stu-id="b3049-108">[in] The path to the file that contains the manifest of the assembly for which the strong name signature will be generated.</span></span>  
  
 `wszKeyContainer`  
 <span data-ttu-id="b3049-109">no O nome do contêiner de chave que contém o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b3049-109">[in] The name of the key container that contains the public/private key pair.</span></span>  
  
 <span data-ttu-id="b3049-110">Se `pbKeyBlob` for NULL, `wszKeyContainer` deverá especificar um contêiner válido no CSP (provedor de serviços de criptografia).</span><span class="sxs-lookup"><span data-stu-id="b3049-110">If `pbKeyBlob` is null, `wszKeyContainer` must specify a valid container within the cryptographic service provider (CSP).</span></span> <span data-ttu-id="b3049-111">Nesse caso, o par de chaves armazenado no contêiner é usado para assinar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="b3049-111">In this case, the key pair stored in the container is used to sign the file.</span></span>  
  
 <span data-ttu-id="b3049-112">Se `pbKeyBlob` não for NULL, o par de chaves será considerado contido no BLOB (objeto binário grande) de chave.</span><span class="sxs-lookup"><span data-stu-id="b3049-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="b3049-113">no Um ponteiro para o par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="b3049-113">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="b3049-114">Esse par está no formato criado pela função de `CryptExportKey` do Win32.</span><span class="sxs-lookup"><span data-stu-id="b3049-114">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="b3049-115">Se `pbKeyBlob` for NULL, o contêiner de chave especificado por `wszKeyContainer` será considerado para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="b3049-115">If `pbKeyBlob` is null, the key container specified by `wszKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="b3049-116">no O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="b3049-116">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbSignatureBlob`  
 <span data-ttu-id="b3049-117">fora Um ponteiro para o local no qual o Common Language Runtime retorna a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b3049-117">[out] A pointer to the location to which the common language runtime returns the signature.</span></span> <span data-ttu-id="b3049-118">Se `ppbSignatureBlob` for NULL, o tempo de execução armazenará a assinatura no arquivo especificado por `wszFilePath`.</span><span class="sxs-lookup"><span data-stu-id="b3049-118">If `ppbSignatureBlob` is null, the runtime stores the signature in the file specified by `wszFilePath`.</span></span>  
  
 <span data-ttu-id="b3049-119">Se `ppbSignatureBlob` não for NULL, a Common Language Runtime alocará espaço para retornar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b3049-119">If `ppbSignatureBlob` is not null, the common language runtime allocates space in which to return the signature.</span></span> <span data-ttu-id="b3049-120">O chamador deve liberar esse espaço usando a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b3049-120">The caller must free this space using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbSignatureBlob`  
 <span data-ttu-id="b3049-121">fora O tamanho, em bytes, da assinatura retornada.</span><span class="sxs-lookup"><span data-stu-id="b3049-121">[out] The size, in bytes, of the returned signature.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="b3049-122">no Um ou mais dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="b3049-122">[in] One or more of the following values:</span></span>  
  
- <span data-ttu-id="b3049-123">`SN_SIGN_ALL_FILES` (0x00000001) – Recomputa todos os hashes para módulos vinculados.</span><span class="sxs-lookup"><span data-stu-id="b3049-123">`SN_SIGN_ALL_FILES` (0x00000001) - Recompute all hashes for linked modules.</span></span>  
  
- <span data-ttu-id="b3049-124">`SN_TEST_SIGN` (0x00000002)-testar o assembly.</span><span class="sxs-lookup"><span data-stu-id="b3049-124">`SN_TEST_SIGN` (0x00000002) - Test-sign the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3049-125">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b3049-125">Return Value</span></span>  
 <span data-ttu-id="b3049-126">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b3049-126">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3049-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3049-127">Remarks</span></span>  
 <span data-ttu-id="b3049-128">Especifique NULL para `wszFilePath` calcular o tamanho da assinatura sem criar a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b3049-128">Specify null for `wszFilePath` to calculate the size of the signature without creating the signature.</span></span>  
  
 <span data-ttu-id="b3049-129">A assinatura pode ser armazenada diretamente no arquivo ou retornada ao chamador.</span><span class="sxs-lookup"><span data-stu-id="b3049-129">The signature can be either stored directly in the file, or returned to the caller.</span></span>  
  
 <span data-ttu-id="b3049-130">Se `SN_SIGN_ALL_FILES` for especificado, mas uma chave pública não estiver incluída (`pbKeyBlob` e `wszFilePath` forem nulas), os hashes para módulos vinculados serão recalculados, mas o assembly não será assinado novamente.</span><span class="sxs-lookup"><span data-stu-id="b3049-130">If `SN_SIGN_ALL_FILES` is specified but a public key is not included (both `pbKeyBlob` and `wszFilePath` are null), hashes for linked modules are recomputed, but the assembly is not re-signed.</span></span>  
  
 <span data-ttu-id="b3049-131">Se `SN_TEST_SIGN` for especificado, o cabeçalho Common Language Runtime não será modificado para indicar que o assembly é assinado com um nome forte.</span><span class="sxs-lookup"><span data-stu-id="b3049-131">If `SN_TEST_SIGN` is specified, the common language runtime header is not modified to indicate that the assembly is signed with a strong name.</span></span>  
  
 <span data-ttu-id="b3049-132">Se a função `StrongNameSignatureGenerationEx` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="b3049-132">If the `StrongNameSignatureGenerationEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3049-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3049-133">Requirements</span></span>  
 <span data-ttu-id="b3049-134">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3049-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3049-135">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="b3049-135">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b3049-136">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b3049-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3049-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3049-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3049-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3049-138">See also</span></span>

- [<span data-ttu-id="b3049-139">Método StrongNameSignatureGenerationEx</span><span class="sxs-lookup"><span data-stu-id="b3049-139">StrongNameSignatureGenerationEx Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [<span data-ttu-id="b3049-140">Método StrongNameSignatureGeneration</span><span class="sxs-lookup"><span data-stu-id="b3049-140">StrongNameSignatureGeneration Method</span></span>](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [<span data-ttu-id="b3049-141">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b3049-141">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
