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
ms.openlocfilehash: 3eac353252f5a97402cbd883895b3e397c39edd6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799173"
---
# <a name="gethashfromhandle-function"></a><span data-ttu-id="76501-102">Função GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="76501-102">GetHashFromHandle Function</span></span>
<span data-ttu-id="76501-103">Gera um hash sobre o conteúdo do arquivo com o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="76501-103">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  
  
 <span data-ttu-id="76501-104">Esta função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="76501-104">This function has been deprecated.</span></span> <span data-ttu-id="76501-105">Em vez disso, use o método [ICLRStrongName:: GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) .</span><span class="sxs-lookup"><span data-stu-id="76501-105">Use the [ICLRStrongName::GetHashFromHandle](../hosting/iclrstrongname-gethashfromhandle-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76501-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76501-106">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76501-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="76501-107">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="76501-108">no O identificador do arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="76501-108">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="76501-109">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="76501-109">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="76501-110">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="76501-110">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="76501-111">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="76501-111">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="76501-112">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="76501-112">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="76501-113">fora O tamanho, em bytes, do retornado `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="76501-113">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76501-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="76501-114">Requirements</span></span>  
 <span data-ttu-id="76501-115">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76501-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76501-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="76501-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="76501-117">**Biblioteca** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="76501-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="76501-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76501-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76501-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76501-119">See also</span></span>

- [<span data-ttu-id="76501-120">Método GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="76501-120">GetHashFromHandle Method</span></span>](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [<span data-ttu-id="76501-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="76501-121">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
