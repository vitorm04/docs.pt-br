---
title: Função CoInitializeEE
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a603bf1badebd2454601780179a8435f33bc70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525172"
---
# <a name="coinitializeee-function"></a><span data-ttu-id="47a15-102">Função CoInitializeEE</span><span class="sxs-lookup"><span data-stu-id="47a15-102">CoInitializeEE Function</span></span>
<span data-ttu-id="47a15-103">Garante que o mecanismo de execução do common language runtime é carregado em um processo.</span><span class="sxs-lookup"><span data-stu-id="47a15-103">Ensures that the common language runtime execution engine is loaded into a process.</span></span> <span data-ttu-id="47a15-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="47a15-104">This function is deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span> <span data-ttu-id="47a15-105">Use o [iclrruntimehost:: Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) método em vez disso.</span><span class="sxs-lookup"><span data-stu-id="47a15-105">Use the [ICLRRuntimeHost::Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47a15-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47a15-106">Syntax</span></span>  
  
```  
HRESULT CoInitializeEE (  
   [in] DWORD fFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47a15-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="47a15-107">Parameters</span></span>  
 `fFlags`  
 <span data-ttu-id="47a15-108">[in] Um dos [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) constantes de enumeração.</span><span class="sxs-lookup"><span data-stu-id="47a15-108">[in] One of the [COINITIEE](../../../../docs/framework/unmanaged-api/metadata/coinitiee-enumeration.md) enumeration constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47a15-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="47a15-109">Return Value</span></span>  
 <span data-ttu-id="47a15-110">Esse método retorna códigos de erro padrão COM conforme definido em Winerror. h e os valores na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="47a15-110">This method returns standard COM error codes as defined in Winerror.h, and the values in the following table.</span></span>  
  
|<span data-ttu-id="47a15-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="47a15-111">Return code</span></span>|<span data-ttu-id="47a15-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="47a15-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="47a15-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="47a15-113">S_OK</span></span>|<span data-ttu-id="47a15-114">O mecanismo de execução foi carregado com êxito.</span><span class="sxs-lookup"><span data-stu-id="47a15-114">The execution engine was loaded successfully.</span></span>|  
|<span data-ttu-id="47a15-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="47a15-115">S_FALSE</span></span>|<span data-ttu-id="47a15-116">O mecanismo de execução já está carregado.</span><span class="sxs-lookup"><span data-stu-id="47a15-116">The execution engine is already loaded.</span></span>|  
|<span data-ttu-id="47a15-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47a15-117">E_FAIL</span></span>|<span data-ttu-id="47a15-118">Não foi possível carregar o mecanismo de execução.</span><span class="sxs-lookup"><span data-stu-id="47a15-118">The execution engine could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47a15-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="47a15-119">Remarks</span></span>  
 <span data-ttu-id="47a15-120">Esse método carrega o mecanismo de execução, se ele não foi carregado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="47a15-120">This method loads the execution engine if it has not been previously loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47a15-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47a15-121">Requirements</span></span>  
 <span data-ttu-id="47a15-122">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47a15-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47a15-123">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="47a15-123">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="47a15-124">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="47a15-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="47a15-125">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47a15-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47a15-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47a15-126">See also</span></span>
- [<span data-ttu-id="47a15-127">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="47a15-127">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
