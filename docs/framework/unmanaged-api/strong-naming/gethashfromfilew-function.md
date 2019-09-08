---
title: Função GetHashFromFileW
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd96b5acb22f63b6e06c981119186680d6593a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799192"
---
# <a name="gethashfromfilew-function"></a><span data-ttu-id="4dac9-102">Função GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="4dac9-102">GetHashFromFileW Function</span></span>
<span data-ttu-id="4dac9-103">Gera um hash sobre o conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="4dac9-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
 <span data-ttu-id="4dac9-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="4dac9-104">This function has been deprecated.</span></span> <span data-ttu-id="4dac9-105">Em vez disso, use o método [ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4dac9-105">Use the [ICLRStrongName::GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dac9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4dac9-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a><span data-ttu-id="4dac9-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4dac9-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="4dac9-108">no O nome Unicode do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="4dac9-108">[in] The Unicode name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="4dac9-109">[entrada, saída] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="4dac9-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="4dac9-110">Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32.</span><span class="sxs-lookup"><span data-stu-id="4dac9-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="4dac9-111">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.</span><span class="sxs-lookup"><span data-stu-id="4dac9-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="4dac9-112">fora Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="4dac9-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="4dac9-113">no O tamanho máximo do buffer apontado por `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4dac9-113">[in] The maximum size of the buffer pointed to by `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="4dac9-114">fora O tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="4dac9-114">[out] The size, in bytes, of `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4dac9-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="4dac9-115">Remarks</span></span>  
 <span data-ttu-id="4dac9-116">Essa função é igual a [GetHashFromFile](gethashfromfile-function.md), exceto que a especificação de nome de arquivo é Unicode em vez de ANSI.</span><span class="sxs-lookup"><span data-stu-id="4dac9-116">This function is the same as [GetHashFromFile](gethashfromfile-function.md), except that the file name specification is Unicode instead of ANSI.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dac9-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4dac9-117">Requirements</span></span>  
 <span data-ttu-id="4dac9-118">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dac9-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dac9-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="4dac9-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="4dac9-120">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4dac9-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4dac9-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dac9-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dac9-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4dac9-122">See also</span></span>

- [<span data-ttu-id="4dac9-123">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="4dac9-123">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="4dac9-124">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="4dac9-124">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="4dac9-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="4dac9-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
