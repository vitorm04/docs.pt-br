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
ms.openlocfilehash: 5e9c0abcd395caf09ebe11e060a4b922e78ad1e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457926"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="457b4-102">Função GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="457b4-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="457b4-103">Obtém um hash do arquivo de assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="457b4-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="457b4-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="457b4-104">This function has been deprecated.</span></span> <span data-ttu-id="457b4-105">Use o [: Gethashfromassemblyfile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="457b4-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457b4-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="457b4-106">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="457b4-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="457b4-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="457b4-108">[in] O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="457b4-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="457b4-109">[out no] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="457b4-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="457b4-110">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="457b4-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="457b4-111">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="457b4-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="457b4-112">[in] O tamanho máximo solicitado da `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="457b4-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="457b4-113">[out] O retornou o tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="457b4-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="457b4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="457b4-114">Requirements</span></span>  
 <span data-ttu-id="457b4-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="457b4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="457b4-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="457b4-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="457b4-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="457b4-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="457b4-118">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="457b4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457b4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="457b4-119">See Also</span></span>  
 [<span data-ttu-id="457b4-120">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="457b4-120">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="457b4-121">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="457b4-121">GetHashFromAssemblyFileW Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfilew-method.md)  
 [<span data-ttu-id="457b4-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="457b4-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
