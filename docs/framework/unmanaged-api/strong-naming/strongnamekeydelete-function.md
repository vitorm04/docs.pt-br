---
title: "Função StrongNameKeyDelete"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameKeyDelete
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameKeyDelete
helpviewer_keywords: StrongNameKeyDelete function [.NET Framework strong naming]
ms.assetid: 313e71e4-1790-4d2f-b68b-5040ebd1c149
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4c7b3ccc9ec1b8cbc81de115f734e1d11e0e0ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamekeydelete-function"></a><span data-ttu-id="59c9a-102">Função StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="59c9a-102">StrongNameKeyDelete Function</span></span>
<span data-ttu-id="59c9a-103">Exclui o contêiner de chave especificado.</span><span class="sxs-lookup"><span data-stu-id="59c9a-103">Deletes the specified key container.</span></span>  
  
 <span data-ttu-id="59c9a-104">Essa função foi preterida.</span><span class="sxs-lookup"><span data-stu-id="59c9a-104">This function has been deprecated.</span></span> <span data-ttu-id="59c9a-105">Use o [Strongnamekeydelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="59c9a-105">Use the [ICLRStrongName::StrongNameKeyDelete](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c9a-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59c9a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameKeyDelete (  
    [in]  LPCWSTR   wszKeyContainer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="59c9a-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59c9a-107">Parameters</span></span>  
 `wszKeyContainer`  
 <span data-ttu-id="59c9a-108">[in] O nome do contêiner de chave para excluir.</span><span class="sxs-lookup"><span data-stu-id="59c9a-108">[in] The name of the key container to delete.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="59c9a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="59c9a-109">Return Value</span></span>  
 <span data-ttu-id="59c9a-110">`true`Após a conclusão bem-sucedida; Caso contrário, `false`.</span><span class="sxs-lookup"><span data-stu-id="59c9a-110">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59c9a-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="59c9a-111">Remarks</span></span>  
 <span data-ttu-id="59c9a-112">Use o [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) função importante um par de chaves pública/privada para um contêiner.</span><span class="sxs-lookup"><span data-stu-id="59c9a-112">Use the [StrongNameKeyInstall](../../../../docs/framework/unmanaged-api/strong-naming/strongnamekeyinstall-function.md) function to importa a public/private key pair into a container.</span></span>  
  
 <span data-ttu-id="59c9a-113">Se o `StrongNameKeyDelete` função não concluída com êxito, chame o [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) função para recuperar o último erro gerado.</span><span class="sxs-lookup"><span data-stu-id="59c9a-113">If the `StrongNameKeyDelete` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59c9a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="59c9a-114">Requirements</span></span>  
 <span data-ttu-id="59c9a-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="59c9a-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59c9a-116">**Cabeçalho:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="59c9a-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="59c9a-117">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="59c9a-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="59c9a-118">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59c9a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59c9a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59c9a-119">See Also</span></span>  
 [<span data-ttu-id="59c9a-120">Método StrongNameKeyDelete</span><span class="sxs-lookup"><span data-stu-id="59c9a-120">StrongNameKeyDelete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeydelete-method.md)  
 [<span data-ttu-id="59c9a-121">Método StrongNameKeyInstall</span><span class="sxs-lookup"><span data-stu-id="59c9a-121">StrongNameKeyInstall Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeyinstall-method.md)  
 [<span data-ttu-id="59c9a-122">Interface ICLRStrongName</span><span class="sxs-lookup"><span data-stu-id="59c9a-122">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
