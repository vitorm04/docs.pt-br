---
title: Função GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
ms.openlocfilehash: cf7667f0f2a0f77cd793e00a5de8b030b0c53ec8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140705"
---
# <a name="gethashfromassemblyfilew-function"></a><span data-ttu-id="45d82-102">Função GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="45d82-102">GetHashFromAssemblyFileW Function</span></span>
<span data-ttu-id="45d82-103">Obtém um hash do arquivo do assembly especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="45d82-103">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="45d82-104">O caminho para o arquivo de assembly deve ser especificado como uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="45d82-104">The path to the assembly file must be specified as a Unicode string.</span></span>  
  
 <span data-ttu-id="45d82-105">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="45d82-105">This function has been deprecated.</span></span> <span data-ttu-id="45d82-106">Em vez disso, use o método [ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="45d82-106">Use the [ICLRStrongName::GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d82-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45d82-107">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45d82-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45d82-108">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="45d82-109">no O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="45d82-109">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="45d82-110">Esse parâmetro deve ser uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="45d82-110">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="45d82-111">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="45d82-111">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="45d82-112">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="45d82-112">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="45d82-113">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="45d82-113">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="45d82-114">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="45d82-114">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="45d82-115">fora O tamanho retornado, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="45d82-115">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d82-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="45d82-116">Requirements</span></span>  
 <span data-ttu-id="45d82-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d82-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d82-118">**Cabeçalho:** StrongName. h</span><span class="sxs-lookup"><span data-stu-id="45d82-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="45d82-119">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="45d82-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="45d82-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45d82-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d82-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45d82-121">See also</span></span>

- [<span data-ttu-id="45d82-122">Método GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="45d82-122">GetHashFromAssemblyFileW Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [<span data-ttu-id="45d82-123">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="45d82-123">GetHashFromAssemblyFile Method</span></span>](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [<span data-ttu-id="45d82-124">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="45d82-124">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
