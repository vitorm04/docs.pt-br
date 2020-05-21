---
title: Método ICLRStrongName::GetHashFromHandle
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromHandle
- ICLRStrongName.StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromHandle
helpviewer_keywords:
- GetHashFromHandle method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::GetHashFromHandle method [.NET Framework hosting]
ms.assetid: 3bedbb7d-3cdd-4175-b370-10ae734062db
topic_type:
- apiref
ms.openlocfilehash: e2d71f7c61b02273bdcaf182f6f79ca3c2a2c75f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762067"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="363f0-102">Método ICLRStrongName::GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="363f0-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="363f0-103">Gera um hash sobre o conteúdo do arquivo que tem o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="363f0-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="363f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="363f0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="363f0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="363f0-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="363f0-106">no O identificador do arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="363f0-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="363f0-107">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="363f0-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="363f0-108">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="363f0-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="363f0-109">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="363f0-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="363f0-110">no O tamanho máximo solicitado de `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="363f0-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="363f0-111">fora O tamanho, em bytes, do retornado `pbHash` .</span><span class="sxs-lookup"><span data-stu-id="363f0-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="363f0-112">Valor Retornado</span><span class="sxs-lookup"><span data-stu-id="363f0-112">Return Value</span></span>  
 <span data-ttu-id="363f0-113">`S_OK`Se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="363f0-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="363f0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="363f0-114">Requirements</span></span>  
 <span data-ttu-id="363f0-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="363f0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="363f0-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="363f0-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="363f0-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="363f0-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="363f0-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="363f0-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="363f0-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="363f0-119">See also</span></span>

- [<span data-ttu-id="363f0-120">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="363f0-120">ICLRStrongName Interface</span></span>](iclrstrongname-interface.md)
