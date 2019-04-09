---
title: Função CreateICeeFileGen
ms.date: 03/30/2017
api_name:
- CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- CreateICeeFileGen
helpviewer_keywords:
- CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 566f73335861a8eb769b21a254e0e93b51a78d02
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151808"
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="9fbe1-102">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="9fbe1-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="9fbe1-103">Cria uma [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="9fbe1-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="9fbe1-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9fbe1-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fbe1-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9fbe1-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fbe1-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9fbe1-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="9fbe1-107">[out] Um ponteiro para o endereço de um novo `ICeeFileGen` objeto.</span><span class="sxs-lookup"><span data-stu-id="9fbe1-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fbe1-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9fbe1-108">Return Value</span></span>  
 <span data-ttu-id="9fbe1-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="9fbe1-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fbe1-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="9fbe1-110">Remarks</span></span>  
 <span data-ttu-id="9fbe1-111">O `ICeeFileGen` objeto é usado para criar common language runtime (CLR) arquivos de PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="9fbe1-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="9fbe1-112">Chame o [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) função para destruir o `ICeeFileGen` objeto quando terminado.</span><span class="sxs-lookup"><span data-stu-id="9fbe1-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fbe1-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9fbe1-113">Requirements</span></span>  
 <span data-ttu-id="9fbe1-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fbe1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fbe1-115">**Cabeçalho:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="9fbe1-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="9fbe1-116">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="9fbe1-116">**Library:** MSCorPE.dll</span></span>  
  
 **<span data-ttu-id="9fbe1-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="9fbe1-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9fbe1-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fbe1-118">See also</span></span>

- [<span data-ttu-id="9fbe1-119">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="9fbe1-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
