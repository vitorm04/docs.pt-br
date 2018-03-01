---
title: "Função StrongNameKeyInstall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- StrongNameKeyInstall
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyInstall
helpviewer_keywords:
- StrongNameKeyInstall function [.NET Framework strong naming]
ms.assetid: e32fd546-7757-4681-be3d-658e93281e50
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9a8dbc84f375b7bbbad47971936650d81c5c63df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeyinstall-function"></a><span data-ttu-id="96edf-102">Função StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="96edf-102">StrongNameKeyInstall Function</span></span>
<span data-ttu-id="96edf-103">Importa um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="96edf-103">Imports a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="96edf-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="96edf-104">This function has been deprecated.</span></span> <span data-ttu-id="96edf-105">Use o [Strongnamekeyinstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="96edf-105">Use the [ICLRStrongName::StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96edf-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96edf-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyInstall (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="96edf-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96edf-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="96edf-108">[in] O nome do contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="96edf-108">[in] The name of the key container.</span></span> <span data-ttu-id="96edf-109">`wszKeyContainer`deve ser uma cadeia de caracteres não vazia.</span><span class="sxs-lookup"><span data-stu-id="96edf-109">`wszKeyContainer` must be a non-empty string.</span></span>  
  
 `pbKeyBlob`  
 <span data-ttu-id="96edf-110">[in] O par de chaves binário.</span><span class="sxs-lookup"><span data-stu-id="96edf-110">[in] The binary key pair.</span></span>  
  
 `cbKeyBlob`  
 <span data-ttu-id="96edf-111">[in] O tamanho, em bytes, de `pbKeyBlob`.</span><span class="sxs-lookup"><span data-stu-id="96edf-111">[in] The size, in bytes, of `pbKeyBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96edf-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="96edf-112">Return Value</span></span>  
 <span data-ttu-id="96edf-113">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="96edf-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="96edf-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="96edf-114">Remarks</span></span>  
 <span data-ttu-id="96edf-115">Use o [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) função para excluir o contêiner de chave.</span><span class="sxs-lookup"><span data-stu-id="96edf-115">Use the [StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeydelete-function.md) function to delete the key container.</span></span>  
  
 <span data-ttu-id="96edf-116">Se o `StrongNameKeyInstall` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="96edf-116">If the `StrongNameKeyInstall` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96edf-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96edf-117">Requirements</span></span>  
 <span data-ttu-id="96edf-118">**Plataformas:** WindSee [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96edf-118">**Platforms:** WindSee [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96edf-119">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="96edf-119">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="96edf-120">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="96edf-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="96edf-121">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96edf-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96edf-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96edf-122">See Also</span></span>  
 [<span data-ttu-id="96edf-123">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="96edf-123">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="96edf-124">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="96edf-124">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="96edf-125">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="96edf-125">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
