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
ms.openlocfilehash: c095c99ee60d6b2ea0e5bce7010a66d40160443d
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899679"
---
# <a name="iclrstrongnamegethashfromhandle-method"></a><span data-ttu-id="ebf1e-102">Método ICLRStrongName::GetHashFromHandle</span><span class="sxs-lookup"><span data-stu-id="ebf1e-102">ICLRStrongName::GetHashFromHandle Method</span></span>
<span data-ttu-id="ebf1e-103">Gera um hash sobre o conteúdo do arquivo que tem o identificador de arquivo especificado, usando o algoritmo de hash especificado.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-103">Generates a hash over the contents of the file that has the specified file handle, using the specified hash algorithm.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ebf1e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ebf1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHashFromHandle (  
    [in]  HANDLE   hFile,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE     *pbHash,  
    [in]  DWORD    cchHash,  
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ebf1e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ebf1e-105">Parameters</span></span>  
 `hFile`  
 <span data-ttu-id="ebf1e-106">no O identificador do arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-106">[in] The handle of the file to be hashed.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="ebf1e-107">[entrada, saída] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-107">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="ebf1e-108">Use zero para o algoritmo padrão.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-108">Use zero for the default algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="ebf1e-109">fora O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-109">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="ebf1e-110">no O tamanho máximo solicitado de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-110">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="ebf1e-111">fora O tamanho, em bytes, do `pbHash`retornado.</span><span class="sxs-lookup"><span data-stu-id="ebf1e-111">[out] The size, in bytes, of the returned `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ebf1e-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="ebf1e-112">Return Value</span></span>  
 <span data-ttu-id="ebf1e-113">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](/windows/win32/seccrypto/common-hresult-values) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="ebf1e-113">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ebf1e-114">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="ebf1e-114">Requirements</span></span>  
 <span data-ttu-id="ebf1e-115">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebf1e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebf1e-116">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="ebf1e-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ebf1e-117">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ebf1e-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebf1e-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebf1e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf1e-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="ebf1e-119">See also</span></span>

- [<span data-ttu-id="ebf1e-120">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="ebf1e-120">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
