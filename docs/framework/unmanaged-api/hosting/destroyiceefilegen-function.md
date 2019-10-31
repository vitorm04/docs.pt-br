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
ms.openlocfilehash: 4eb878b61b72378bc6870af7f2cd09f0b6943b13
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136496"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="9ccf7-102">Função DestroyICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="9ccf7-102">DestroyICeeFileGen Function</span></span>
<span data-ttu-id="9ccf7-103">Destrói um objeto [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) .</span><span class="sxs-lookup"><span data-stu-id="9ccf7-103">Destroys an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="9ccf7-104">Essa função foi preterida no .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ccf7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9ccf7-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9ccf7-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9ccf7-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="9ccf7-107">no O objeto `ICeeFileGen` a ser destruído.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ccf7-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="9ccf7-108">Return Value</span></span>  
 <span data-ttu-id="9ccf7-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="9ccf7-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9ccf7-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ccf7-110">Remarks</span></span>  
 <span data-ttu-id="9ccf7-111">`DestroyICeeFileGen` destrói o objeto `ICeeFileGen` criado pela função [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) .</span><span class="sxs-lookup"><span data-stu-id="9ccf7-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ccf7-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ccf7-112">Requirements</span></span>  
 <span data-ttu-id="9ccf7-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ccf7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ccf7-114">**Cabeçalho:** ICeeFileGen. h</span><span class="sxs-lookup"><span data-stu-id="9ccf7-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="9ccf7-115">**Biblioteca:** MSCorPE. dll</span><span class="sxs-lookup"><span data-stu-id="9ccf7-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="9ccf7-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ccf7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ccf7-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ccf7-117">See also</span></span>

- [<span data-ttu-id="9ccf7-118">Funções de hospedagem CLR preteridas</span><span class="sxs-lookup"><span data-stu-id="9ccf7-118">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
