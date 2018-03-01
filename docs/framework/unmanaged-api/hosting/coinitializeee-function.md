---
title: "Função CoInitializeEE"
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
- CoInitializeEE
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeEE
helpviewer_keywords:
- CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0ca564830411a9df0d47cc9765958286bbd40f96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="coinitializeee-function"></a><span data-ttu-id="72ea9-102">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="72ea9-102">CoInitializeEE Function</span></span>
<span data-ttu-id="72ea9-103">Garante que o mecanismo de execução do common language runtime está carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="72ea9-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="72ea9-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="72ea9-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="72ea9-105">Use o [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="72ea9-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ea9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="72ea9-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72ea9-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="72ea9-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="72ea9-108">[in] Uma da [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) constantes de enumeração.</span><span class="sxs-lookup"><span data-stu-id="72ea9-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72ea9-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="72ea9-109">Return Value</span></span>  
 <span data-ttu-id="72ea9-110">Esse método retorna códigos de erro padrão COM conforme definido em Winerror. h e os valores na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="72ea9-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="72ea9-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="72ea9-111">Return code</span></span>|<span data-ttu-id="72ea9-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="72ea9-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="72ea9-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="72ea9-113">S_OK</span></span>|<span data-ttu-id="72ea9-114">O mecanismo de execução foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="72ea9-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="72ea9-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="72ea9-115">S_FALSE</span></span>|<span data-ttu-id="72ea9-116">O mecanismo de execução já foi carregado.</span><span class="sxs-lookup"><span data-stu-id="72ea9-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="72ea9-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72ea9-117">E_FAIL</span></span>|<span data-ttu-id="72ea9-118">Não foi possível carregar o mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="72ea9-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ea9-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="72ea9-119">Remarks</span></span>  
 <span data-ttu-id="72ea9-120">Esse método carrega o mecanismo de execução, se ele não foi carregado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="72ea9-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ea9-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="72ea9-121">Requirements</span></span>  
 <span data-ttu-id="72ea9-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72ea9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72ea9-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="72ea9-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="72ea9-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="72ea9-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="72ea9-125">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72ea9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ea9-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72ea9-126">See Also</span></span>  
 [<span data-ttu-id="72ea9-127">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="72ea9-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
