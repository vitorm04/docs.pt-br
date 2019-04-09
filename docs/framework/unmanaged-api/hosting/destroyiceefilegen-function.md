---
title: Função DestroyICeeFileGen
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37ff40e1c009b8e1e0509a4a3333d5a2a70bbfd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159881"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="746d6-102">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="746d6-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="746d6-103">Destrói um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="746d6-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="746d6-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="746d6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="746d6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="746d6-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="746d6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="746d6-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="746d6-107">[in] O `ICeeFileGen` objeto a ser destruído.</span><span class="sxs-lookup"><span data-stu-id="746d6-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="746d6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="746d6-108">Return Value</span></span>  
 <span data-ttu-id="746d6-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="746d6-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="746d6-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="746d6-110">Remarks</span></span>  
 `DestroyICeeFileGen` <span data-ttu-id="746d6-111">destrói a `ICeeFileGen` objeto criado pelo [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="746d6-111">destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="746d6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="746d6-112">Requirements</span></span>  
 <span data-ttu-id="746d6-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="746d6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="746d6-114">**Cabeçalho:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="746d6-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="746d6-115">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="746d6-115">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="746d6-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="746d6-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="746d6-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="746d6-117">See also</span></span>

- [<span data-ttu-id="746d6-118">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="746d6-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
