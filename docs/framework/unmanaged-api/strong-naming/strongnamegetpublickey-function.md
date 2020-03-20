---
title: Função StrongNameGetPublicKey
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
ms.openlocfilehash: fcdd4a3f07b4499fd2388b5d165c409da9150466
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176923"
---
# <a name="strongnamegetpublickey-function"></a><span data-ttu-id="2ed18-102">Função StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="2ed18-102">StrongNameGetPublicKey Function</span></span>
<span data-ttu-id="2ed18-103">Obtém a chave pública de um par de chaves pública/privada.</span><span class="sxs-lookup"><span data-stu-id="2ed18-103">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="2ed18-104">O par de chaves pode ser fornecido como um nome de contêiner chave dentro de um provedor de serviços criptográficos (CSP) ou como uma coleção bruta de bytes.</span><span class="sxs-lookup"><span data-stu-id="2ed18-104">The key pair can be supplied either as a key container name within a cryptographic service provider (CSP) or as a raw collection of bytes.</span></span>  
  
 <span data-ttu-id="2ed18-105">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="2ed18-105">This function has been deprecated.</span></span> <span data-ttu-id="2ed18-106">Use o método [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="2ed18-106">Use the [ICLRStrongName::StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed18-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ed18-107">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ed18-108">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2ed18-108">Parameters</span></span>  
 `szKeyContainer`  
 <span data-ttu-id="2ed18-109">[em] O nome do recipiente de chave que contém o par de chaves público/privado.</span><span class="sxs-lookup"><span data-stu-id="2ed18-109">[in] The name of the key container that contains the public/private key pair.</span></span> <span data-ttu-id="2ed18-110">Se `pbKeyBlob` for `szKeyContainer` nulo, deve especificar um recipiente válido dentro do CSP.</span><span class="sxs-lookup"><span data-stu-id="2ed18-110">If `pbKeyBlob` is null, `szKeyContainer` must specify a valid container within the CSP.</span></span> <span data-ttu-id="2ed18-111">Neste caso, `StrongNameGetPublicKey` extrai a chave pública do par de chaves armazenado no recipiente.</span><span class="sxs-lookup"><span data-stu-id="2ed18-111">In this case, `StrongNameGetPublicKey` extracts the public key from the key pair stored in the container.</span></span>  
  
 <span data-ttu-id="2ed18-112">Se `pbKeyBlob` não for nulo, presume-se que o par de chaves esteja contido no objeto grande binário chave (BLOB).</span><span class="sxs-lookup"><span data-stu-id="2ed18-112">If `pbKeyBlob` is not null, the key pair is assumed to be contained in the key binary large object (BLOB).</span></span>  
  
 <span data-ttu-id="2ed18-113">As teclas devem ser teclas de assinatura Rivest-Shamir-Adleman (RSA) de 1024 bits.</span><span class="sxs-lookup"><span data-stu-id="2ed18-113">The keys must be 1024-bit Rivest-Shamir-Adleman (RSA) signing keys.</span></span> <span data-ttu-id="2ed18-114">Nenhum outro tipo de chaves é suportado neste momento.</span><span class="sxs-lookup"><span data-stu-id="2ed18-114">No other types of keys are supported at this time.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="2ed18-115">[em] Um ponteiro para o par de tecla público/privado.</span><span class="sxs-lookup"><span data-stu-id="2ed18-115">[in] A pointer to the public/private key pair.</span></span> <span data-ttu-id="2ed18-116">Este par está no formato criado pela `CryptExportKey` função Win32.</span><span class="sxs-lookup"><span data-stu-id="2ed18-116">This pair is in the format created by the Win32 `CryptExportKey` function.</span></span> <span data-ttu-id="2ed18-117">Se `pbKeyBlob` for nulo, o `szKeyContainer` recipiente de chave especificado por é assumido para conter o par de chaves.</span><span class="sxs-lookup"><span data-stu-id="2ed18-117">If `pbKeyBlob` is null, the key container specified by `szKeyContainer` is assumed to contain the key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="2ed18-118">[em] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="2ed18-118">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="2ed18-119">[fora] A chave pública devolvida BLOB.</span><span class="sxs-lookup"><span data-stu-id="2ed18-119">[out] The returned public key BLOB.</span></span> <span data-ttu-id="2ed18-120">O `ppbPublicKeyBlob` parâmetro é alocado pelo tempo de execução do idioma comum e devolvido ao chamador.</span><span class="sxs-lookup"><span data-stu-id="2ed18-120">The `ppbPublicKeyBlob` parameter is allocated by the common language runtime and returned to the caller.</span></span> <span data-ttu-id="2ed18-121">O chamador deve liberar a memória usando a função [StrongNameFreeBuffer.](strongnamefreebuffer-function.md)</span><span class="sxs-lookup"><span data-stu-id="2ed18-121">The caller must free the memory by using the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="2ed18-122">[fora] O tamanho da chave pública devolvida BLOB.</span><span class="sxs-lookup"><span data-stu-id="2ed18-122">[out] The size of the returned public key BLOB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ed18-123">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2ed18-123">Return Value</span></span>  
 <span data-ttu-id="2ed18-124">`true`em conclusão bem sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="2ed18-124">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ed18-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ed18-125">Remarks</span></span>  
 <span data-ttu-id="2ed18-126">A chave pública está contida em uma estrutura [PublicKeyBlob.](publickeyblob-structure.md)</span><span class="sxs-lookup"><span data-stu-id="2ed18-126">The public key is contained in a [PublicKeyBlob](publickeyblob-structure.md) structure.</span></span>  
  
 <span data-ttu-id="2ed18-127">Se `StrongNameGetPublicKey` a função não for concluída com sucesso, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="2ed18-127">If the `StrongNameGetPublicKey` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ed18-128">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ed18-128">Requirements</span></span>  
 <span data-ttu-id="2ed18-129">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ed18-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ed18-130">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="2ed18-130">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="2ed18-131">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ed18-131">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2ed18-132">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ed18-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ed18-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="2ed18-133">See also</span></span>

- [<span data-ttu-id="2ed18-134">Método StrongNameGetPublicKey</span><span class="sxs-lookup"><span data-stu-id="2ed18-134">StrongNameGetPublicKey Method</span></span>](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [<span data-ttu-id="2ed18-135">Método StrongNameTokenFromPublicKey</span><span class="sxs-lookup"><span data-stu-id="2ed18-135">StrongNameTokenFromPublicKey Method</span></span>](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [<span data-ttu-id="2ed18-136">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="2ed18-136">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="2ed18-137">Estrutura PublicKeyBlob</span><span class="sxs-lookup"><span data-stu-id="2ed18-137">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)
