---
title: "Método ICLRStrongName::StrongNameTokenFromAssembly"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName.StrongNameTokenFromAssembly
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0b236fe3b041277401c2983cf229981253c01328
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="5fa63-102">Método ICLRStrongName::StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="5fa63-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="5fa63-103">Cria um token de nome forte do arquivo de assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="5fa63-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fa63-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5fa63-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fa63-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5fa63-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="5fa63-106">[in] O caminho para o arquivo PE (executável portátil) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="5fa63-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="5fa63-107">[out] O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="5fa63-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="5fa63-108">[out] O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="5fa63-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5fa63-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5fa63-109">Return Value</span></span>  
 <span data-ttu-id="5fa63-110">`S_OK`Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="5fa63-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fa63-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="5fa63-111">Remarks</span></span>  
 <span data-ttu-id="5fa63-112">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="5fa63-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="5fa63-113">O token é um hash de 64 bits que é criado a partir de chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="5fa63-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="5fa63-114">O token é uma parte do nome forte do assembly e pode ser lidos dos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="5fa63-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="5fa63-115">Depois que o token é criado, você deve chamar o [Iclrstrongname](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="5fa63-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fa63-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5fa63-116">Requirements</span></span>  
 <span data-ttu-id="5fa63-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fa63-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fa63-118">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="5fa63-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="5fa63-119">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5fa63-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5fa63-120">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fa63-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa63-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fa63-121">See Also</span></span>  
 [<span data-ttu-id="5fa63-122">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="5fa63-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)  
 [<span data-ttu-id="5fa63-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="5fa63-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
