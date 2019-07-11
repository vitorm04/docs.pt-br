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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4839f098a41e0d2b8e87616791b69ffd83e139f0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748197"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="433cc-102">Método ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="433cc-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="433cc-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="433cc-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="433cc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="433cc-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="433cc-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="433cc-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="433cc-106">[in] Um ponteiro para o endereço do bloco de memória a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="433cc-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="433cc-107">[in] O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="433cc-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="433cc-108">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="433cc-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="433cc-109">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="433cc-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="433cc-110">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="433cc-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="433cc-111">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="433cc-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="433cc-112">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="433cc-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="433cc-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="433cc-113">Return Value</span></span>  
 <span data-ttu-id="433cc-114">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="433cc-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="433cc-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="433cc-115">Requirements</span></span>  
 <span data-ttu-id="433cc-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="433cc-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="433cc-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="433cc-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="433cc-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="433cc-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="433cc-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="433cc-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="433cc-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="433cc-120">See also</span></span>

- [<span data-ttu-id="433cc-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="433cc-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
