---
title: Método ICLRStrongName::GetHashFromBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromBlob
helpviewer_keywords:
- ICLRStrongName::GetHashFromBlob method [.NET Framework hosting]
- GetHashFromBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: f91d0f89-f356-49ac-aafb-50fad963c13d
topic_type:
- apiref
ms.openlocfilehash: 0c9adcc252fe16c95da8b2afca45bb2ee5dc545a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135200"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="95c2b-102">Método ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="95c2b-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="95c2b-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="95c2b-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c2b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95c2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95c2b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="95c2b-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="95c2b-106">no Um ponteiro para o endereço do bloco de memória com hash.</span><span class="sxs-lookup"><span data-stu-id="95c2b-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="95c2b-107">no O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="95c2b-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="95c2b-108">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="95c2b-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="95c2b-109">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="95c2b-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="95c2b-110">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="95c2b-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="95c2b-111">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="95c2b-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="95c2b-112">fora O tamanho, em bytes, do `pbHash`retornado.</span><span class="sxs-lookup"><span data-stu-id="95c2b-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="95c2b-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="95c2b-113">Return Value</span></span>  
 <span data-ttu-id="95c2b-114">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="95c2b-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c2b-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="95c2b-115">Requirements</span></span>  
 <span data-ttu-id="95c2b-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c2b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c2b-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="95c2b-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="95c2b-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95c2b-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c2b-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c2b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c2b-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="95c2b-120">See also</span></span>

- [<span data-ttu-id="95c2b-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="95c2b-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
