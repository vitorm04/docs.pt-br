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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20bafd0dfc455538292e47ca33508c251ad68614
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458169"
---
# <a name="strongnametokenfromassemblyex-function"></a><span data-ttu-id="80d53-102">Função StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="80d53-102">StrongNameTokenFromAssemblyEx Function</span></span>
<span data-ttu-id="80d53-103">Cria um token de nome forte do arquivo de assembly especificado e retorna a chave pública que representa o token.</span><span class="sxs-lookup"><span data-stu-id="80d53-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
 <span data-ttu-id="80d53-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="80d53-104">This function has been deprecated.</span></span> <span data-ttu-id="80d53-105">Use o [: Strongnametokenfromassemblyex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="80d53-105">Use the [ICLRStrongName::StrongNameTokenFromAssemblyEx](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80d53-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80d53-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="80d53-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="80d53-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="80d53-108">[in] O caminho para o arquivo PE (executável portátil) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="80d53-108">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="80d53-109">[out] O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="80d53-109">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="80d53-110">[out] O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="80d53-110">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="80d53-111">[out] A chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="80d53-111">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="80d53-112">[out] O tamanho, em bytes, da chave pública.</span><span class="sxs-lookup"><span data-stu-id="80d53-112">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="80d53-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="80d53-113">Return Value</span></span>  
 <span data-ttu-id="80d53-114">`true` Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="80d53-114">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80d53-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="80d53-115">Remarks</span></span>  
 <span data-ttu-id="80d53-116">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="80d53-116">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="80d53-117">O token é um hash de 64 bits que é criado a partir de chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="80d53-117">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="80d53-118">O token é uma parte do nome forte do assembly e pode ser lidos dos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="80d53-118">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="80d53-119">Depois que a chave é recuperada e o token é criado, você deve chamar o [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) função para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="80d53-119">After the key is retrieved and the token is created, you should call the [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md) function to release the allocated memory.</span></span>  
  
 <span data-ttu-id="80d53-120">Se o `StrongNameTokenFromAssemblyEx` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="80d53-120">If the `StrongNameTokenFromAssemblyEx` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80d53-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="80d53-121">Requirements</span></span>  
 <span data-ttu-id="80d53-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80d53-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80d53-123">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="80d53-123">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="80d53-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="80d53-124">**Library:** Included as a resource in mscoree.dll</span></span>  
  
 <span data-ttu-id="80d53-125">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80d53-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80d53-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80d53-126">See Also</span></span>  
 [<span data-ttu-id="80d53-127">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="80d53-127">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="80d53-128">Método StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="80d53-128">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="80d53-129">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="80d53-129">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
