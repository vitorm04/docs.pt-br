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
ms.openlocfilehash: daf674c0340998c0fd518e0f1af721bbe9ff653c
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490477"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="8b00d-102">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="8b00d-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="8b00d-103">Destrói um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="8b00d-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="8b00d-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8b00d-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b00d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b00d-105">Syntax</span></span>  
  
```  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b00d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8b00d-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="8b00d-107">[in] O `ICeeFileGen` objeto a ser destruído.</span><span class="sxs-lookup"><span data-stu-id="8b00d-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b00d-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8b00d-108">Return Value</span></span>  
 <span data-ttu-id="8b00d-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="8b00d-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b00d-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b00d-110">Remarks</span></span>  
 <span data-ttu-id="8b00d-111">`DestroyICeeFileGen` destrói a `ICeeFileGen` objeto criado pelo [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="8b00d-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b00d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b00d-112">Requirements</span></span>  
 <span data-ttu-id="8b00d-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b00d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b00d-114">**Cabeçalho:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="8b00d-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="8b00d-115">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="8b00d-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="8b00d-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b00d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b00d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b00d-117">See also</span></span>

- [<span data-ttu-id="8b00d-118">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="8b00d-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
