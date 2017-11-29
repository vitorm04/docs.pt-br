---
title: "Função GetRealProcAddress"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetRealProcAddress
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: GetRealProcAddress
helpviewer_keywords: GetRealProcAddress function [.NET Framework hosting]
ms.assetid: f1f2fab1-400b-488f-95f2-d49c4fca3556
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 53e51bcf72f1a59f5c471564022d0d8c415381a6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="getrealprocaddress-function"></a><span data-ttu-id="41186-102">Função GetRealProcAddress</span><span class="sxs-lookup"><span data-stu-id="41186-102">GetRealProcAddress Function</span></span>
<span data-ttu-id="41186-103">Obtém o endereço da função especificada é exportado da versão instalada mais recente do common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="41186-103">Gets the address of the specified function that is exported from the latest installed version of the common language runtime (CLR).</span></span>  
  
 <span data-ttu-id="41186-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="41186-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41186-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41186-105">Syntax</span></span>  
  
```  
HRESULT GetRealProcAddress (  
    [in]  LPCSTR  pwszProcName,   
    [out] VOID  **ppv  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41186-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="41186-106">Parameters</span></span>  
 `pwszProcName`  
 <span data-ttu-id="41186-107">[in] O nome da função.</span><span class="sxs-lookup"><span data-stu-id="41186-107">[in] The name of the function.</span></span>  
  
 `ppv`  
 <span data-ttu-id="41186-108">[out] O local que recebe um ponteiro para o endereço da função.</span><span class="sxs-lookup"><span data-stu-id="41186-108">[out] The location that receives a pointer to the address of the function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="41186-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="41186-109">Return Value</span></span>  
 <span data-ttu-id="41186-110">Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos seguintes valores definidos no corerror.</span><span class="sxs-lookup"><span data-stu-id="41186-110">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values defined in CorError.h.</span></span>  
  
|<span data-ttu-id="41186-111">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="41186-111">Return code</span></span>|<span data-ttu-id="41186-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="41186-112">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="41186-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="41186-113">S_OK</span></span>|<span data-ttu-id="41186-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="41186-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="41186-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="41186-115">E_POINTER</span></span>|<span data-ttu-id="41186-116">`ppv` não é válido.</span><span class="sxs-lookup"><span data-stu-id="41186-116">`ppv` is not valid.</span></span>|  
|<span data-ttu-id="41186-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="41186-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="41186-118">A função não é exportada do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="41186-118">The function is not exported from the runtime.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="41186-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41186-119">Requirements</span></span>  
 <span data-ttu-id="41186-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41186-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41186-121">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="41186-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="41186-122">**Biblioteca:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="41186-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="41186-123">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41186-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41186-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41186-124">See Also</span></span>  
 [<span data-ttu-id="41186-125">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="41186-125">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
