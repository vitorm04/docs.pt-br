---
title: Função GetHashFromHandle
ms.date: 03/30/2017
api_name:
- GetHashFromHandle
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle function [.NET Framework strong naming]
ms.assetid: 9e00337f-b307-4602-9bc3-965a8dbf02cd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 48dd987896536006fe81bc01528cadb507123e27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59203399"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="f2bbf-102">Função GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="f2bbf-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="f2bbf-103">Gera um hash sobre o conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="f2bbf-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-104">This function has been deprecated.</span></span> <span data-ttu-id="f2bbf-105">Use o [iclrstrongname:: Gethashfromhandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-105">Use the [ICLRStrongName::GetHashFromHandle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2bbf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f2bbf-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2bbf-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f2bbf-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="f2bbf-108">[in] O identificador do arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="f2bbf-109">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="f2bbf-110">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="f2bbf-111">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="f2bbf-112">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="f2bbf-113">[out] O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="f2bbf-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2bbf-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f2bbf-114">Requirements</span></span>  
 <span data-ttu-id="f2bbf-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2bbf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2bbf-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f2bbf-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f2bbf-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="f2bbf-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f2bbf-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2bbf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2bbf-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f2bbf-119">See also</span></span>

- [<span data-ttu-id="f2bbf-120">Método GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="f2bbf-120">GetHashFromHandle Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="f2bbf-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="f2bbf-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
