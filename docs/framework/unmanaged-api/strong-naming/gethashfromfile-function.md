---
title: Função GetHashFromFile
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799221"
---
# <a name="gethashfromfile-function"></a><span data-ttu-id="cf2c6-102">Função GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="cf2c6-102">GetHashFromFile Function</span></span>
<span data-ttu-id="cf2c6-103">Gera um hash sobre o conteúdo do arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-103">Generates a hash over the contents of the specified file.</span></span>  
  
 <span data-ttu-id="cf2c6-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-104">This function has been deprecated.</span></span> <span data-ttu-id="cf2c6-105">Em vez disso, use o método [ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cf2c6-105">Use the [ICLRStrongName::GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf2c6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf2c6-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf2c6-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf2c6-107">Parameters</span></span>  
 `szFilePath`  
 <span data-ttu-id="cf2c6-108">no O nome do arquivo para hash.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-108">[in] The name of the file to hash.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="cf2c6-109">[entrada, saída] O algoritmo a ser usado ao gerar o hash.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-109">[in, out] The algorithm to use when generating the hash.</span></span> <span data-ttu-id="cf2c6-110">Os algoritmos válidos são aqueles definidos pelo CryptoAPI do Win32.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-110">Valid algorithms are those defined by the Win32 CryptoAPI.</span></span> <span data-ttu-id="cf2c6-111">Se `piHashAlg` for definido como 0, o algoritmo padrão CALG_SHA-1 será usado.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-111">If `piHashAlg` is set to 0, the default algorithm CALG_SHA-1 is used.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="cf2c6-112">fora Uma matriz de bytes que contém o hash gerado.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-112">[out] A byte array containing the generated hash.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="cf2c6-113">no O tamanho máximo do buffer que `pbHash` aponta para.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-113">[in] The maximum size of the buffer that `pbHash` points to.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="cf2c6-114">fora O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-114">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf2c6-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf2c6-115">Remarks</span></span>  
 <span data-ttu-id="cf2c6-116">Essa função é a mesma que [GetHashFromFileW](gethashfromfilew-function.md), exceto que a especificação de nome de arquivo é ANSI em vez de Unicode.</span><span class="sxs-lookup"><span data-stu-id="cf2c6-116">This function is the same as [GetHashFromFileW](gethashfromfilew-function.md), except that the file name specification is ANSI instead of Unicode.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf2c6-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf2c6-117">Requirements</span></span>  
 <span data-ttu-id="cf2c6-118">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf2c6-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf2c6-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="cf2c6-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="cf2c6-120">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cf2c6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cf2c6-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf2c6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf2c6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf2c6-122">See also</span></span>

- [<span data-ttu-id="cf2c6-123">Método GetHashFromFile</span><span class="sxs-lookup"><span data-stu-id="cf2c6-123">GetHashFromFile Method</span></span>](../hosting/iclrstrongname-gethashfromfile-method.md)
- [<span data-ttu-id="cf2c6-124">Método GetHashFromFileW</span><span class="sxs-lookup"><span data-stu-id="cf2c6-124">GetHashFromFileW Method</span></span>](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [<span data-ttu-id="cf2c6-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="cf2c6-125">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
