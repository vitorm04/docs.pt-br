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
ms.openlocfilehash: b42079d138e754996470e07b884d49c1ebb625c3
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901161"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="ecddb-102">Método ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="ecddb-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="ecddb-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="ecddb-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecddb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ecddb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ecddb-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ecddb-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="ecddb-106">no Um ponteiro para o endereço do bloco de memória com hash.</span><span class="sxs-lookup"><span data-stu-id="ecddb-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="ecddb-107">no O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="ecddb-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ecddb-108">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="ecddb-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ecddb-109">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="ecddb-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ecddb-110">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="ecddb-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ecddb-111">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ecddb-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ecddb-112">fora O tamanho, em bytes, do `pbHash`retornado.</span><span class="sxs-lookup"><span data-stu-id="ecddb-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecddb-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ecddb-113">Return Value</span></span>  
 <span data-ttu-id="ecddb-114">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="ecddb-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecddb-115">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ecddb-115">Requirements</span></span>  
 <span data-ttu-id="ecddb-116">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecddb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecddb-117">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ecddb-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ecddb-118">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ecddb-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ecddb-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecddb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecddb-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="ecddb-120">See also</span></span>

- [<span data-ttu-id="ecddb-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ecddb-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
