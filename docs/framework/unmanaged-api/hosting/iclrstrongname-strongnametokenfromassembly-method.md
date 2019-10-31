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
ms.openlocfilehash: 0e7e49fae24ff7e12c5a8d9cac5e814f7a7ae813
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092587"
---
# <a name="iclrstrongnamestrongnametokenfromassembly-method"></a><span data-ttu-id="91713-102">Método ICLRStrongName::StrongNameTokenFromAssembly</span><span class="sxs-lookup"><span data-stu-id="91713-102">ICLRStrongName::StrongNameTokenFromAssembly Method</span></span>
<span data-ttu-id="91713-103">Cria um token de nome forte do arquivo do assembly especificado.</span><span class="sxs-lookup"><span data-stu-id="91713-103">Creates a strong name token from the specified assembly file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91713-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91713-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91713-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="91713-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="91713-106">no O caminho para o arquivo executável portátil (PE) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="91713-106">[in] The path to the portable executable (PE) file for the assembly.</span></span>  
  
 `ppbStrongNameToken`  
 <span data-ttu-id="91713-107">fora O token de nome forte retornado.</span><span class="sxs-lookup"><span data-stu-id="91713-107">[out] The returned strong name token.</span></span>  
  
 `pcbStrongNameToken`  
 <span data-ttu-id="91713-108">fora O tamanho, em bytes, do token de nome forte.</span><span class="sxs-lookup"><span data-stu-id="91713-108">[out] The size, in bytes, of the strong name token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91713-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="91713-109">Return Value</span></span>  
 <span data-ttu-id="91713-110">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="91713-110">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91713-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="91713-111">Remarks</span></span>  
 <span data-ttu-id="91713-112">Um token de nome forte é a forma abreviada de uma chave pública.</span><span class="sxs-lookup"><span data-stu-id="91713-112">A strong name token is the shortened form of a public key.</span></span> <span data-ttu-id="91713-113">O token é um hash de 64 bits que é criado a partir da chave pública usada para assinar o assembly.</span><span class="sxs-lookup"><span data-stu-id="91713-113">The token is a 64-bit hash that is created from the public key used to sign the assembly.</span></span> <span data-ttu-id="91713-114">O token é uma parte do nome forte para o assembly e pode ser lido nos metadados do assembly.</span><span class="sxs-lookup"><span data-stu-id="91713-114">The token is a part of the strong name for the assembly, and can be read from the assembly metadata.</span></span>  
  
 <span data-ttu-id="91713-115">Depois que o token é criado, você deve chamar o método [ICLRStrongName:: StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) para liberar a memória alocada.</span><span class="sxs-lookup"><span data-stu-id="91713-115">After the token is created, you should call the [ICLRStrongName::StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) method to release the allocated memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91713-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="91713-116">Requirements</span></span>  
 <span data-ttu-id="91713-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91713-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91713-118">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="91713-118">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="91713-119">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="91713-119">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="91713-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91713-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91713-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91713-121">See also</span></span>

- [<span data-ttu-id="91713-122">Método StrongNameTokenFromAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="91713-122">StrongNameTokenFromAssemblyEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [<span data-ttu-id="91713-123">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="91713-123">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
