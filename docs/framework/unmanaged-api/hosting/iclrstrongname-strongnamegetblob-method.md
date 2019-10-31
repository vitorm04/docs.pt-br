---
title: Método ICLRStrongName::StrongNameGetBlob
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
ms.openlocfilehash: 9d7f1a71658b53a1b4167c767eb89c873308421b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135123"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="36018-102">Método ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="36018-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="36018-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="36018-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36018-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="36018-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36018-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="36018-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="36018-106">no Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="36018-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="36018-107">no O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="36018-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="36018-108">[entrada, saída] O tamanho máximo solicitado, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="36018-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="36018-109">No retorno, o tamanho real, em bytes, de `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="36018-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36018-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="36018-110">Return Value</span></span>  
 <span data-ttu-id="36018-111">`S_OK` se o método foi concluído com êxito; caso contrário, um valor HRESULT que indica falha (consulte [valores de HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para uma lista).</span><span class="sxs-lookup"><span data-stu-id="36018-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36018-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="36018-112">Requirements</span></span>  
 <span data-ttu-id="36018-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36018-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36018-114">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="36018-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="36018-115">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="36018-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36018-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36018-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36018-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="36018-117">See also</span></span>

- [<span data-ttu-id="36018-118">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="36018-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="36018-119">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="36018-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
