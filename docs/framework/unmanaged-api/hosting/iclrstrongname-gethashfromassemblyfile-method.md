---
title: Método ICLRStrongName::GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFile method [.NET Framework hosting]
- GetHashFromAssemblyFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 0b67ea03-d474-4605-acaa-57455790250c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a8d9e7d593c2a8a9cce798724b2705dee21a740e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44072032"
---
# <a name="iclrstrongnamegethashfromassemblyfile-method"></a><span data-ttu-id="c365e-102">Método ICLRStrongName::GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="c365e-102">ICLRStrongName::GetHashFromAssemblyFile Method</span></span>
<span data-ttu-id="c365e-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="c365e-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c365e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c365e-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c365e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c365e-105">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="c365e-106">[in] O caminho para o arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="c365e-106">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="c365e-107">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="c365e-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="c365e-108">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="c365e-108">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="c365e-109">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="c365e-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="c365e-110">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c365e-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="c365e-111">[out] O retornado tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="c365e-111">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c365e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c365e-112">Return Value</span></span>  
 <span data-ttu-id="c365e-113">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="c365e-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c365e-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c365e-114">Requirements</span></span>  
 <span data-ttu-id="c365e-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c365e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c365e-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="c365e-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="c365e-117">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="c365e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c365e-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c365e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c365e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c365e-119">See Also</span></span>  
 [<span data-ttu-id="c365e-120">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="c365e-120">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="c365e-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="c365e-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
