---
title: Método ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7686a84759f8ac40a123d2c9a7b8f1b9b8096cb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749912"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="38bf2-102">Método ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="38bf2-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="38bf2-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="38bf2-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38bf2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38bf2-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38bf2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38bf2-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="38bf2-106">[in] O caminho para o arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="38bf2-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="38bf2-107">Esse parâmetro deve ser uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="38bf2-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="38bf2-108">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="38bf2-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="38bf2-109">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="38bf2-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="38bf2-110">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="38bf2-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="38bf2-111">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="38bf2-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="38bf2-112">[out] O retornado tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="38bf2-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38bf2-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="38bf2-113">Return Value</span></span>  
 <span data-ttu-id="38bf2-114">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="38bf2-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38bf2-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="38bf2-115">Requirements</span></span>  
 <span data-ttu-id="38bf2-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38bf2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38bf2-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="38bf2-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="38bf2-118">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="38bf2-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="38bf2-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38bf2-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38bf2-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38bf2-120">See Also</span></span>  
 [<span data-ttu-id="38bf2-121">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="38bf2-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="38bf2-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="38bf2-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
