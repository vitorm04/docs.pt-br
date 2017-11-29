---
title: "Função CreateICeeFileGen"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="d4442-102">Função CreateICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="d4442-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="d4442-103">Cria um [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) objeto.</span><span class="sxs-lookup"><span data-stu-id="d4442-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="d4442-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d4442-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4442-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d4442-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4442-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d4442-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="d4442-107">[out] Um ponteiro para o endereço de um novo `ICeeFileGen` objeto.</span><span class="sxs-lookup"><span data-stu-id="d4442-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4442-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d4442-108">Return Value</span></span>  
 <span data-ttu-id="d4442-109">Esse método retorna códigos de erro COM padrão.</span><span class="sxs-lookup"><span data-stu-id="d4442-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4442-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d4442-110">Remarks</span></span>  
 <span data-ttu-id="d4442-111">O `ICeeFileGen` objeto é usado para criar o common language runtime (CLR) arquivos de PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="d4442-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="d4442-112">Chamar o [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) função destruir o `ICeeFileGen` objeto quando terminado.</span><span class="sxs-lookup"><span data-stu-id="d4442-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4442-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d4442-113">Requirements</span></span>  
 <span data-ttu-id="d4442-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4442-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4442-115">**Cabeçalho:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="d4442-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="d4442-116">**Biblioteca:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="d4442-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="d4442-117">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4442-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4442-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4442-118">See Also</span></span>  
 [<span data-ttu-id="d4442-119">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="d4442-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
