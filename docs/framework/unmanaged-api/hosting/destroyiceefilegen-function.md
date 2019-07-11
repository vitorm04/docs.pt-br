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
ms.openlocfilehash: ab4560774edce49341c86dd9446e38701db7fa62
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769822"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="c26f4-102">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="c26f4-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="c26f4-103">Destrói um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="c26f4-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="c26f4-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="c26f4-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c26f4-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c26f4-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c26f4-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c26f4-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="c26f4-107">[in] O `ICeeFileGen` objeto a ser destruído.</span><span class="sxs-lookup"><span data-stu-id="c26f4-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c26f4-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c26f4-108">Return Value</span></span>  
 <span data-ttu-id="c26f4-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="c26f4-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c26f4-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="c26f4-110">Remarks</span></span>  
 <span data-ttu-id="c26f4-111">`DestroyICeeFileGen` destrói a `ICeeFileGen` objeto criado pelo [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="c26f4-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c26f4-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c26f4-112">Requirements</span></span>  
 <span data-ttu-id="c26f4-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c26f4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c26f4-114">**Cabeçalho:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="c26f4-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="c26f4-115">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="c26f4-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="c26f4-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c26f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c26f4-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c26f4-117">See also</span></span>

- [<span data-ttu-id="c26f4-118">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="c26f4-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
