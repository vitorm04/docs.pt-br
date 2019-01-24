---
title: Função GetHashFromAssemblyFile
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFile
helpviewer_keywords:
- GetHashFromAssemblyFile function [.NET Framework strong naming]
ms.assetid: 751ed69f-b7ab-4e07-80de-e17ca9319b0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83e3ba8644af1f630b5c9ad5268ec44750badc88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682035"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="04da5-102">Função GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="04da5-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="04da5-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="04da5-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="04da5-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="04da5-104">This function has been deprecated.</span></span> <span data-ttu-id="04da5-105">Use o [iclrstrongname:: Gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="04da5-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04da5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04da5-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04da5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="04da5-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="04da5-108">[in] O caminho para o arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="04da5-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="04da5-109">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="04da5-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="04da5-110">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="04da5-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="04da5-111">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="04da5-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="04da5-112">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="04da5-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="04da5-113">[out] O retornado tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="04da5-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04da5-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="04da5-114">Requirements</span></span>  
 <span data-ttu-id="04da5-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04da5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04da5-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="04da5-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="04da5-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="04da5-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04da5-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04da5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04da5-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04da5-119">See also</span></span>
- [<span data-ttu-id="04da5-120">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="04da5-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="04da5-121">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="04da5-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="04da5-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="04da5-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
