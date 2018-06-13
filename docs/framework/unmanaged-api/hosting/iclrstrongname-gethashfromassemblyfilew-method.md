---
title: Método ICLRStrongName::GetHashFromAssemblyFileW
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW
helpviewer_keywords:
- ICLRStrongName::GetHashFromAssemblyFileW method [.NET Framework hosting]
- GetHashFromAssemblyFileW method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5d0b44a2-5a14-44a2-9a0e-e8682fd4e106
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36e4f07f04968579be2e42efad666b0453cc4796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434785"
---
# <a name="iclrstrongnamegethashfromassemblyfilew-method"></a><span data-ttu-id="37fd0-102">Método ICLRStrongName::GetHashFromAssemblyFileW</span><span class="sxs-lookup"><span data-stu-id="37fd0-102">ICLRStrongName::GetHashFromAssemblyFileW Method</span></span>
<span data-ttu-id="37fd0-103">Gera um hash com base no conteúdo do arquivo especificado por uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="37fd0-103">Generates a hash over the contents of the file specified by a Unicode string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37fd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37fd0-104">Syntax</span></span>  
  
```  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="37fd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="37fd0-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="37fd0-106">[in] O caminho para o arquivo a ser transformado em hash.</span><span class="sxs-lookup"><span data-stu-id="37fd0-106">[in] The path to the file to be hashed.</span></span> <span data-ttu-id="37fd0-107">Esse parâmetro deve ser uma cadeia de caracteres Unicode.</span><span class="sxs-lookup"><span data-stu-id="37fd0-107">This parameter must be a Unicode string.</span></span>  
  
 `piHashAlg`  
 <span data-ttu-id="37fd0-108">[out no] Uma constante que especifica o algoritmo de hash.</span><span class="sxs-lookup"><span data-stu-id="37fd0-108">[in, out] A constant that specifies the hash algorithm.</span></span> <span data-ttu-id="37fd0-109">Use zero para o algoritmo de hash padrão.</span><span class="sxs-lookup"><span data-stu-id="37fd0-109">Use zero for the default hash algorithm.</span></span>  
  
 `pbHash`  
 <span data-ttu-id="37fd0-110">[out] O buffer de hash retornado.</span><span class="sxs-lookup"><span data-stu-id="37fd0-110">[out] The returned hash buffer.</span></span>  
  
 `cchHash`  
 <span data-ttu-id="37fd0-111">[in] O tamanho máximo solicitado da `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="37fd0-111">[in] The requested maximum size of `pbHash`.</span></span>  
  
 `pchHash`  
 <span data-ttu-id="37fd0-112">[out] O retornou o tamanho, em bytes, de `pbHash`.</span><span class="sxs-lookup"><span data-stu-id="37fd0-112">[out] The returned size, in bytes, of `pbHash`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37fd0-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="37fd0-113">Return Value</span></span>  
 <span data-ttu-id="37fd0-114">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="37fd0-114">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37fd0-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="37fd0-115">Requirements</span></span>  
 <span data-ttu-id="37fd0-116">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37fd0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37fd0-117">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="37fd0-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="37fd0-118">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="37fd0-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37fd0-119">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37fd0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37fd0-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37fd0-120">See Also</span></span>  
 [<span data-ttu-id="37fd0-121">Método GetHashFromAssemblyFile</span><span class="sxs-lookup"><span data-stu-id="37fd0-121">GetHashFromAssemblyFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromassemblyfile-method.md)  
 [<span data-ttu-id="37fd0-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="37fd0-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
