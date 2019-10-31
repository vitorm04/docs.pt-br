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
ms.openlocfilehash: 866b34acae333f043d8e13f4d0ebd55f32046334
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140721"
---
# <a name="gethashfromassemblyfile-function"></a><span data-ttu-id="bdb4c-102">Função GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="bdb4c-102">GetHashFromAssemblyFile Function</span></span>
<span data-ttu-id="bdb4c-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="bdb4c-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-104">This function has been deprecated.</span></span> <span data-ttu-id="bdb4c-105">Em vez disso, use o método [ICLRStrongName:: GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bdb4c-105">Use the [ICLRStrongName::GetHashFromAssemblyFile](../hosting/iclrstrongname-gethashfromassemblyfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb4c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bdb4c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdb4c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bdb4c-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="bdb4c-108">no O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-108">[in] The path to the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="bdb4c-109">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="bdb4c-110">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-110">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="bdb4c-111">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="bdb4c-112">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="bdb4c-113">fora O tamanho retornado, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="bdb4c-113">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb4c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bdb4c-114">Requirements</span></span>  
 <span data-ttu-id="bdb4c-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdb4c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb4c-116">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="bdb4c-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="bdb4c-117">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bdb4c-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdb4c-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb4c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb4c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdb4c-119">See also</span></span>

- [<span data-ttu-id="bdb4c-120">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="bdb4c-120">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="bdb4c-121">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="bdb4c-121">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="bdb4c-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="bdb4c-122">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
