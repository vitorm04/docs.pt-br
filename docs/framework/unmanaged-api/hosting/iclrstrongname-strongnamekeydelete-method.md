---
title: Método ICLRStrongName::StrongNameKeyDelete
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyDelete method [.NET Framework hosting]
ms.assetid: 0163412f-f617-4428-89e0-03992fec31e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7636391e97d79befba3b80a9c4a952e5f64840c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467031"
---
# <a name="iclrstrongnamestrongnamekeydelete-method"></a><span data-ttu-id="4257c-102">Método ICLRStrongName::StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="4257c-102">ICLRStrongName::StrongNameKeyDelete Method</span></span>
<span data-ttu-id="4257c-103">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="4257c-103">Deletes the specified key container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4257c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4257c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4257c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4257c-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="4257c-106">[in] O nome de excluir o contêiner de chaves.</span><span class="sxs-lookup"><span data-stu-id="4257c-106">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4257c-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4257c-107">Return Value</span></span>  
 <span data-ttu-id="4257c-108">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="4257c-108">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4257c-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4257c-109">Remarks</span></span>  
 <span data-ttu-id="4257c-110">Use o [iclrstrongname:: Strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) método para importar um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="4257c-110">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method to import a public/private key pair into a container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4257c-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4257c-111">Requirements</span></span>  
 <span data-ttu-id="4257c-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4257c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4257c-113">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="4257c-113">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4257c-114">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="4257c-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4257c-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4257c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4257c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4257c-116">See also</span></span>
- [<span data-ttu-id="4257c-117">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="4257c-117">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)
- [<span data-ttu-id="4257c-118">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="4257c-118">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
