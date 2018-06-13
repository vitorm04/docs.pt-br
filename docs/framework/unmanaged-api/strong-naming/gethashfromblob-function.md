---
title: Função GetHashFromBlob
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 427d93a9aff527d36720c4199782fa104a66f8d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455027"
---
# <a name="gethashfromblob-function"></a><span data-ttu-id="e55fd-102">Função GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="e55fd-102">GetHashFromBlob Function</span></span>
<span data-ttu-id="e55fd-103">Obtém um hash do assembly no endereço de memória especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="e55fd-103">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="e55fd-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="e55fd-104">This function has been deprecated.</span></span> <span data-ttu-id="e55fd-105">Use o [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="e55fd-105">Use the [ICLRStronName::GetHashFromBlob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e55fd-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e55fd-106">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="e55fd-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e55fd-107">Parameters</span></span>  
 `pbBlob`  
 <span data-ttu-id="e55fd-108">[in] Um ponteiro para o endereço do bloco de memória a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="e55fd-108">[in] A pointer to the address of the memory block to be hashed.</span></span>  
  
 `cchBlob`  
 <span data-ttu-id="e55fd-109">[in] O comprimento, em bytes, do bloco de memória.</span><span class="sxs-lookup"><span data-stu-id="e55fd-109">[in] The length, in bytes, of the memory block.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="e55fd-110">[out no] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="e55fd-110">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="e55fd-111">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="e55fd-111">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="e55fd-112">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="e55fd-112">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="e55fd-113">[in] O tamanho máximo solicitado da `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e55fd-113">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="e55fd-114">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="e55fd-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e55fd-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e55fd-115">Requirements</span></span>  
 <span data-ttu-id="e55fd-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e55fd-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e55fd-117">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="e55fd-117">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="e55fd-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="e55fd-118">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e55fd-119">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e55fd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e55fd-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e55fd-120">See Also</span></span>  
 [<span data-ttu-id="e55fd-121">Método GetHashFromBlob</span><span class="sxs-lookup"><span data-stu-id="e55fd-121">GetHashFromBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)  
 [<span data-ttu-id="e55fd-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="e55fd-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
