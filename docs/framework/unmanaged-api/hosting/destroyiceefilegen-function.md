---
title: "Função DestroyICeeFileGen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: DestroyICeeFileGen
helpviewer_keywords: DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 11f0bd03532668196f85713459fe103f9120c82e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="b711f-102">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="b711f-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="b711f-103">Destrói um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="b711f-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="b711f-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b711f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b711f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b711f-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b711f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b711f-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="b711f-107">[in] O `ICeeFileGen` objeto destruir.</span><span class="sxs-lookup"><span data-stu-id="b711f-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b711f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b711f-108">Return Value</span></span>  
 <span data-ttu-id="b711f-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="b711f-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b711f-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="b711f-110">Remarks</span></span>  
 <span data-ttu-id="b711f-111">`DestroyICeeFileGen`destrói a `ICeeFileGen` objeto criado pelo [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="b711f-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b711f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b711f-112">Requirements</span></span>  
 <span data-ttu-id="b711f-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b711f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b711f-114">**Cabeçalho:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="b711f-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="b711f-115">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="b711f-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="b711f-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b711f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b711f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b711f-117">See Also</span></span>  
 [<span data-ttu-id="b711f-118">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="b711f-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
