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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4621a7d143d401d4cb620ac17c31e4ee5f13837
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46577646"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="92814-102">Método ICLRStrongName::StrongNameGetBlob</span><span class="sxs-lookup"><span data-stu-id="92814-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="92814-103">Preenche o buffer especificado com a representação binária do arquivo executável no endereço especificado.</span><span class="sxs-lookup"><span data-stu-id="92814-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92814-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92814-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92814-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="92814-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="92814-106">[in] Um caminho válido para o arquivo executável a ser carregado.</span><span class="sxs-lookup"><span data-stu-id="92814-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="92814-107">[in] O buffer no qual carregar o arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="92814-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="92814-108">[no, out] O solicitada tamanho máximo, em bytes, da `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="92814-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="92814-109">Após o retorno, o tamanho real, em bytes, do `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="92814-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92814-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="92814-110">Return Value</span></span>  
 <span data-ttu-id="92814-111">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="92814-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92814-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92814-112">Requirements</span></span>  
 <span data-ttu-id="92814-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92814-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92814-114">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="92814-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="92814-115">**Biblioteca:** incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="92814-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92814-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92814-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92814-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92814-117">See Also</span></span>  
 [<span data-ttu-id="92814-118">Método StrongNameGetBlobFromImage</span><span class="sxs-lookup"><span data-stu-id="92814-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="92814-119">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="92814-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
