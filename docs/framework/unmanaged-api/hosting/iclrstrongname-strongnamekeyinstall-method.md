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
ms.openlocfilehash: 415df9928572e095c529119bf2e726fa383577b0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224943"
---
# <a name="iclrstrongnamestrongnamekeyinstall-method"></a><span data-ttu-id="adac2-102">Método ICLRStrongName::StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="adac2-102">ICLRStrongName::StrongNameKeyInstall Method</span></span>
<span data-ttu-id="adac2-103">Importa um par de chaves públicas/privadas em um contêiner.</span><span class="sxs-lookup"><span data-stu-id="adac2-103">Imports a public/private key pair into a container.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adac2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="adac2-104">Syntax</span></span>  
  
```  
HRESULT StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adac2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="adac2-105">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="adac2-106">[in] O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="adac2-106">[in] The name of the key container.</span></span> `wszKeyContainer` <span data-ttu-id="adac2-107">deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="adac2-107">must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="adac2-108">[in] O par de chaves binário.</span><span class="sxs-lookup"><span data-stu-id="adac2-108">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="adac2-109">[in] O tamanho, em bytes, do `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="adac2-109">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adac2-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="adac2-110">Return Value</span></span>  
 `S_OK` <span data-ttu-id="adac2-111">Se o método foi concluída com êxito; Caso contrário, um valor HRESULT que indica uma falha (consulte [valores HRESULT comuns](https://go.microsoft.com/fwlink/?LinkId=213878) para obter uma lista).</span><span class="sxs-lookup"><span data-stu-id="adac2-111">if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adac2-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="adac2-112">Remarks</span></span>  
 <span data-ttu-id="adac2-113">Use o [iclrstrongname:: Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) método para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="adac2-113">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method to delete the key container.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adac2-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="adac2-114">Requirements</span></span>  
 <span data-ttu-id="adac2-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adac2-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adac2-116">**Cabeçalho:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="adac2-116">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="adac2-117">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="adac2-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="adac2-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="adac2-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="adac2-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adac2-119">See also</span></span>

- [<span data-ttu-id="adac2-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="adac2-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)
- [<span data-ttu-id="adac2-121">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="adac2-121">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
