---
title: Método ICLRStrongName::GetHashFromHandle
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20c5f6bbb58b85f42ec00e356eccc5fb41ce813c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036227"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="707bb-102">Método ICLRStrongName::GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="707bb-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="707bb-103">Gera um hash sobre o conteúdo do arquivo que tem o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="707bb-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="707bb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="707bb-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="707bb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="707bb-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="707bb-106">[in] O identificador do arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="707bb-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="707bb-107">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="707bb-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="707bb-108">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="707bb-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="707bb-109">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="707bb-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="707bb-110">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="707bb-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="707bb-111">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="707bb-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="707bb-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="707bb-112">Return Value</span></span>  
 <span data-ttu-id="707bb-113">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="707bb-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="707bb-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="707bb-114">Requirements</span></span>  
 <span data-ttu-id="707bb-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="707bb-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="707bb-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="707bb-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="707bb-117">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="707bb-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="707bb-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="707bb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707bb-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="707bb-119">See Also</span></span>  
 [<span data-ttu-id="707bb-120">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="707bb-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
