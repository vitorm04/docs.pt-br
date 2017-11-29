---
title: "Função CoInitializeEE"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CoInitializeEE
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: CoInitializeEE
helpviewer_keywords: CoInitializeEE function [.NET Framework hosting]
ms.assetid: 7e42a928-5068-4ba6-b8c3-806551a01fa8
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 429d055ec0853d04f794b063a76a395d98aceb4f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="coinitializeee-function"></a><span data-ttu-id="554a1-102">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="554a1-102">CoInitializeEE Function</span></span>
<span data-ttu-id="554a1-103">Garante que o mecanismo de execução do common language runtime está carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="554a1-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="554a1-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="554a1-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="554a1-105">Use o [Iclrruntimehost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="554a1-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554a1-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="554a1-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="554a1-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="554a1-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="554a1-108">[in] Uma da [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) constantes de enumeração.</span><span class="sxs-lookup"><span data-stu-id="554a1-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="554a1-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="554a1-109">Return Value</span></span>  
 <span data-ttu-id="554a1-110">Esse método retorna códigos de erro padrão COM conforme definido em Winerror. h e os valores na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="554a1-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="554a1-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="554a1-111">Return code</span></span>|<span data-ttu-id="554a1-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="554a1-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="554a1-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="554a1-113">S_OK</span></span>|<span data-ttu-id="554a1-114">O mecanismo de execução foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="554a1-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="554a1-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="554a1-115">S_FALSE</span></span>|<span data-ttu-id="554a1-116">O mecanismo de execução já foi carregado.</span><span class="sxs-lookup"><span data-stu-id="554a1-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="554a1-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="554a1-117">E_FAIL</span></span>|<span data-ttu-id="554a1-118">Não foi possível carregar o mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="554a1-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="554a1-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="554a1-119">Remarks</span></span>  
 <span data-ttu-id="554a1-120">Esse método carrega o mecanismo de execução, se ele não foi carregado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="554a1-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554a1-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="554a1-121">Requirements</span></span>  
 <span data-ttu-id="554a1-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="554a1-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="554a1-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="554a1-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="554a1-124">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="554a1-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="554a1-125">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="554a1-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554a1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="554a1-126">See Also</span></span>  
 [<span data-ttu-id="554a1-127">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="554a1-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
