---
title: Método ICLRStrongName::StrongNameKeyInstall
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyInstall
helpviewer_keywords:
- ICLRStrongName::StrongNameKeyInstall method [.NET Framework hosting]
- StrongNameKeyInstall method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 5c15cf3b-164c-49d1-8e57-e42949d55acf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 572afc5eb9ec3cf52199e5ad74406c876485461c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434084"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="6f39c-102">Método ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="6f39c-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="6f39c-103">Importa um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="6f39c-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f39c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f39c-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f39c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f39c-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="6f39c-106">[in] O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="6f39c-106">[in] The name of the key container.</span></span> <span data-ttu-id="6f39c-107">`wszKeyContainer` deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="6f39c-107">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="6f39c-108">[in] O par de chaves binário.</span><span class="sxs-lookup"><span data-stu-id="6f39c-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="6f39c-109">[in] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="6f39c-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f39c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f39c-110">Return Value</span></span>  
 <span data-ttu-id="6f39c-111">`S_OK` Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](http://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="6f39c-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](http://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f39c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f39c-112">Remarks</span></span>  
 <span data-ttu-id="6f39c-113">Use o [Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) método para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="6f39c-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f39c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f39c-114">Requirements</span></span>  
 <span data-ttu-id="6f39c-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f39c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f39c-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6f39c-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6f39c-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="6f39c-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f39c-118">**Versões do .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f39c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f39c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f39c-119">See Also</span></span>  
 [<span data-ttu-id="6f39c-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="6f39c-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="6f39c-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="6f39c-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
