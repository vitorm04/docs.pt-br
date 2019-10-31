---
title: Função StrongNameTokenFromAssemblyEx
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssemblyEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx function [.NET Framework strong naming]
ms.assetid: 67a8a9f2-dee3-44b2-a1c0-f307a3bdf90f
topic_type:
- apiref
ms.openlocfilehash: 8b7866b92be3195b0a767a823a0d7fb1c0aa4918
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73104243"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="3c1f2-102">Função StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="3c1f2-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="3c1f2-103">Cria um token de nome forte a partir do arquivo de assembly especificado e retorna a chave pública que o token representa.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="3c1f2-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-104">This function has been deprecated.</span></span> <span data-ttu-id="3c1f2-105">Em vez disso, use o método [ICLRStrongName:: StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3c1f2-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c1f2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c1f2-106">Syntax</span></span>  
  
```cpp  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c1f2-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3c1f2-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="3c1f2-108">no O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="3c1f2-109">fora O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="3c1f2-110">fora O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="3c1f2-111">fora A chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="3c1f2-112">fora O tamanho, em bytes, da chave pública.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c1f2-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3c1f2-113">Return Value</span></span>  
 <span data-ttu-id="3c1f2-114">`true` após a conclusão bem-sucedida; caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c1f2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c1f2-115">Remarks</span></span>  
 <span data-ttu-id="3c1f2-116">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="3c1f2-117">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="3c1f2-118">O token é uma parte do nome forte para o assembly e pode ser lido nos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="3c1f2-119">Depois que a chave for recuperada e o token for criado, você deverá chamar a função [StrongNameFreeBuffer](strongnamefreebuffer-function.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="3c1f2-120">Se a função `StrongNameTokenFromAssemblyEx` não for concluída com êxito, chame a função [StrongNameErrorInfo](strongnameerrorinfo-function.md) para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="3c1f2-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c1f2-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3c1f2-121">Requirements</span></span>  
 <span data-ttu-id="3c1f2-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c1f2-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c1f2-123">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="3c1f2-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="3c1f2-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="3c1f2-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="3c1f2-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c1f2-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c1f2-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3c1f2-126">See also</span></span>

- [<span data-ttu-id="3c1f2-127">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="3c1f2-127">StrongNameTokenFromAssemblyEx Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="3c1f2-128">Método StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="3c1f2-128">StrongNameTokenFromAssembly Method</span></span>](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [<span data-ttu-id="3c1f2-129">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="3c1f2-129">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
