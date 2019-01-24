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
ms.openlocfilehash: 8b85f8ffade19cee8f0703af823d91a6ea7bf50b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710204"
---
# <a name="iclrstrongnamegethashfromblob-method"></a><span data-ttu-id="df807-102">Método ICLRStrongName::GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="df807-102">ICLRStrongName::GetHashFromBlob Method</span></span>
<span data-ttu-id="df807-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="df807-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df807-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df807-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromBlob (  
    [in]  BYTE    *pbBlob,  
    [in]  DWORD   cchBlob,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE    *pbHash,  
    [in]  DWORD   cchHash,  
    [out] DWORD   *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df807-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="df807-105">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="df807-106">[in] Um ponteiro para o endereço do bloco de memória a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="df807-106">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="df807-107">[in] O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="df807-107">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="df807-108">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="df807-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="df807-109">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="df807-109">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="df807-110">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="df807-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="df807-111">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="df807-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="df807-112">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="df807-112">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df807-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="df807-113">Return Value</span></span>  
 <span data-ttu-id="df807-114">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="df807-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df807-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df807-115">Requirements</span></span>  
 <span data-ttu-id="df807-116">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df807-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df807-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="df807-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="df807-118">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="df807-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="df807-119">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df807-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df807-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df807-120">See also</span></span>
- [<span data-ttu-id="df807-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="df807-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
