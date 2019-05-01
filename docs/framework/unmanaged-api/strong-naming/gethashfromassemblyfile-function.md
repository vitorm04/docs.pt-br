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
ms.openlocfilehash: e56a509d08b19cf449177984e7b59481eb7b09a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049395"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="9f6d6-102">Função GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="9f6d6-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="9f6d6-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="9f6d6-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-104">This function has been deprecated.</span></span> <span data-ttu-id="9f6d6-105">Use o [iclrstrongname:: Gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f6d6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f6d6-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f6d6-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f6d6-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="9f6d6-108">[in] O caminho para o arquivo a ser transformada em hash.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="9f6d6-109">[no, out] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="9f6d6-110">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="9f6d6-111">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="9f6d6-112">[in] O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="9f6d6-113">[out] O retornado tamanho, em bytes, do `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="9f6d6-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f6d6-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9f6d6-114">Requirements</span></span>  
 <span data-ttu-id="9f6d6-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f6d6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f6d6-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="9f6d6-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="9f6d6-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="9f6d6-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9f6d6-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f6d6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f6d6-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f6d6-119">See also</span></span>

- [<span data-ttu-id="9f6d6-120">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="9f6d6-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="9f6d6-121">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="9f6d6-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="9f6d6-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="9f6d6-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
