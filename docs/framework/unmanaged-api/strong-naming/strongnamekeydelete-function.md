---
title: "Função StrongNameKeyDelete"
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
- StrongNameKeyDelete
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyDelete
helpviewer_keywords:
- StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d3acd8ae5f330e23642a679962a04ccb4f7e8ec6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="b5f2f-102">Função StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="b5f2f-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="b5f2f-103">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="b5f2f-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-104">This function has been deprecated.</span></span> <span data-ttu-id="b5f2f-105">Use o [Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5f2f-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5f2f-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b5f2f-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5f2f-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="b5f2f-108">[in] O nome do contêiner de chave para excluir.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5f2f-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b5f2f-109">Return Value</span></span>  
 <span data-ttu-id="b5f2f-110">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5f2f-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="b5f2f-111">Remarks</span></span>  
 <span data-ttu-id="b5f2f-112">Use o [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) função importante um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="b5f2f-113">Se o `StrongNameKeyDelete` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="b5f2f-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b5f2f-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5f2f-114">Requirements</span></span>  
 <span data-ttu-id="b5f2f-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5f2f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5f2f-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="b5f2f-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="b5f2f-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="b5f2f-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b5f2f-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b5f2f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5f2f-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5f2f-119">See Also</span></span>  
 [<span data-ttu-id="b5f2f-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="b5f2f-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="b5f2f-121">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="b5f2f-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="b5f2f-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="b5f2f-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
