---
title: "Método ICLRStrongName::StrongNameTokenFromAssemblyEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromAssemblyEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromAssemblyEx
helpviewer_keywords:
- StrongNameTokenFromAssemblyEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameTokenFromAssemblyEx method [.NET Framework hosting]
ms.assetid: 648ea90e-5e60-40a0-a56a-3e61bf2fba7c
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5b8b3437d8c07cd57a4791995890cab1b06aafc6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongnamestrongnametokenfromassemblyex-method"></a><span data-ttu-id="12c13-102">Método ICLRStrongName::StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="12c13-102">ICLRStrongName::StrongNameTokenFromAssemblyEx Method</span></span>
<span data-ttu-id="12c13-103">Cria um token de nome forte do arquivo de assembly especificado e retorna a chave pública que representa o token.</span><span class="sxs-lookup"><span data-stu-id="12c13-103">Creates a strong name token from the specified assembly file, and returns the public key that the token represents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c13-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12c13-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssemblyEx (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12c13-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="12c13-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="12c13-106">[in] O caminho para o arquivo PE (executável portátil) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="12c13-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="12c13-107">[out] O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="12c13-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="12c13-108">[out] O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="12c13-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
 `ppbPublicKeyBlob`  
 <span data-ttu-id="12c13-109">[out] A chave pública retornada.</span><span class="sxs-lookup"><span data-stu-id="12c13-109">[out] The returned public key.</span></span>  
  
 `pcbPublicKeyBlob`  
 <span data-ttu-id="12c13-110">[out] O tamanho, em bytes, da chave pública.</span><span class="sxs-lookup"><span data-stu-id="12c13-110">[out] The size, in bytes, of the public key.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12c13-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="12c13-111">Return Value</span></span>  
 <span data-ttu-id="12c13-112">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="12c13-112">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12c13-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="12c13-113">Remarks</span></span>  
 <span data-ttu-id="12c13-114">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="12c13-114">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="12c13-115">O token é um hash de 64 bits que é criado a partir de chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="12c13-115">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="12c13-116">O token é uma parte do nome forte do assembly e pode ser lidos dos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="12c13-116">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="12c13-117">Depois que a chave é recuperada e o token é criado, você deve chamar o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="12c13-117">After the key is retrieved and the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12c13-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="12c13-118">Requirements</span></span>  
 <span data-ttu-id="12c13-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12c13-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12c13-120">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="12c13-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="12c13-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="12c13-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12c13-122">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12c13-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12c13-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="12c13-123">See Also</span></span>  
 [<span data-ttu-id="12c13-124">Método StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="12c13-124">StrongNameTokenFromAssembly Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)  
 [<span data-ttu-id="12c13-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="12c13-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
