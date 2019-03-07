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
ms.openlocfilehash: 9688635532e0ccc35ff8826a53da80738bfc528e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470010"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="fee37-102">Método ICLRStrongName::GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="fee37-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="fee37-103">Gera um hash sobre o conteúdo do arquivo que tem o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="fee37-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee37-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fee37-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fee37-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fee37-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="fee37-106">[in] O identificador do arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="fee37-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="fee37-107">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="fee37-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="fee37-108">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="fee37-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="fee37-109">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="fee37-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="fee37-110">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fee37-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="fee37-111">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="fee37-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fee37-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fee37-112">Return Value</span></span>  
 <span data-ttu-id="fee37-113">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="fee37-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee37-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fee37-114">Requirements</span></span>  
 <span data-ttu-id="fee37-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee37-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee37-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="fee37-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="fee37-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="fee37-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fee37-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee37-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee37-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fee37-119">See also</span></span>
- [<span data-ttu-id="fee37-120">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="fee37-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
