---
title: Método ICLRStrongName::StrongNameTokenFromAssembly
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromAssembly method [.NET Framework hosting]
- StrongNameTokenFromAssembly method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: fc725afb-b66b-4015-aa44-1c0d1304197f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a2931c16e13d08c1e3e7d5b62e6583102a1b8cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229245"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="7086a-102">Método ICLRStrongName::StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="7086a-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="7086a-103">Cria um token de nome forte do arquivo do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="7086a-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7086a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7086a-104">Syntax</span></span>  
  
```  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7086a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7086a-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="7086a-106">[in] O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="7086a-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="7086a-107">[out] O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="7086a-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="7086a-108">[out] O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="7086a-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7086a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7086a-109">Return Value</span></span>  
 `S_OK` <span data-ttu-id="7086a-110">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="7086a-110">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7086a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="7086a-111">Remarks</span></span>  
 <span data-ttu-id="7086a-112">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="7086a-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="7086a-113">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="7086a-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="7086a-114">O token é uma parte do nome forte para o assembly e os metadados do assembly pode ser lido.</span><span class="sxs-lookup"><span data-stu-id="7086a-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="7086a-115">Depois que o token é criado, você deve chamar o [iclrstrongname:: Strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) método para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="7086a-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7086a-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7086a-116">Requirements</span></span>  
 <span data-ttu-id="7086a-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7086a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7086a-118">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="7086a-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="7086a-119">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="7086a-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7086a-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7086a-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7086a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7086a-121">See also</span></span>

- [<span data-ttu-id="7086a-122">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="7086a-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="7086a-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="7086a-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
