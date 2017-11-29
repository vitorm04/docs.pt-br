---
title: "Função LoadStringRC"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadStringRC
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: LoadStringRC
helpviewer_keywords: LoadStringRC function [.NET Framework hosting]
ms.assetid: 752e49b4-987c-4c28-a118-1a0c1ed510c5
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bc93adf575af7f2803b20f24a3261a447772ffd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="loadstringrc-function"></a><span data-ttu-id="a493f-102">Função LoadStringRC</span><span class="sxs-lookup"><span data-stu-id="a493f-102">LoadStringRC Function</span></span>
<span data-ttu-id="a493f-103">Converte um valor HRESULT em uma mensagem de erro usando a cultura padrão do thread atual.</span><span class="sxs-lookup"><span data-stu-id="a493f-103">Translates an HRESULT value into an error message by using the default culture of the current thread.</span></span>  
  
 <span data-ttu-id="a493f-104">Essa função foi preterida no [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a493f-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a493f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a493f-105">Syntax</span></span>  
  
```  
HRESULT LoadStringRC (  
    [in]  UINT    iResourceID,   
    [out] LPWSTR  szBuffer,   
    [in]  int     iMax,   
    [in]  int     bQuiet  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a493f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a493f-106">Parameters</span></span>  
 `iResourceID`  
 <span data-ttu-id="a493f-107">[in] Um HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a493f-107">[in] An HRESULT.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="a493f-108">[out] Um buffer que contém a mensagem de erro após a conclusão bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a493f-108">[out] A buffer that contains the error message upon successful completion.</span></span>  
  
 `iMax`  
 <span data-ttu-id="a493f-109">[in] O tamanho do buffer de mensagem de erro.</span><span class="sxs-lookup"><span data-stu-id="a493f-109">[in] The size of the error message buffer.</span></span>  
  
 `bQuiet`  
 <span data-ttu-id="a493f-110">[in] Ignorado.</span><span class="sxs-lookup"><span data-stu-id="a493f-110">[in] Ignored.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a493f-111">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a493f-111">Return Value</span></span>  
 <span data-ttu-id="a493f-112">Esse método retorna códigos de erro do modelo de objeto de componente (COM) padrão, conforme definido no Winerror. H, além dos valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="a493f-112">This method returns standard Component Object Model (COM) error codes, as defined in WinError.h, in addition to the following values.</span></span>  
  
|<span data-ttu-id="a493f-113">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="a493f-113">Return code</span></span>|<span data-ttu-id="a493f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="a493f-114">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a493f-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="a493f-115">S_OK</span></span>|<span data-ttu-id="a493f-116">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="a493f-116">The method completed successfully.</span></span>|  
|<span data-ttu-id="a493f-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a493f-117">E_INVALIDARG</span></span>|<span data-ttu-id="a493f-118">`szBuffer`é nulo ou `iMax` é zero (0).</span><span class="sxs-lookup"><span data-stu-id="a493f-118">`szBuffer` is null or `iMax` is zero (0).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a493f-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="a493f-119">Remarks</span></span>  
 <span data-ttu-id="a493f-120">Se o método não for concluída com êxito, `szBuffer` contém uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="a493f-120">If the method does not complete successfully, `szBuffer` contains an empty string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a493f-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a493f-121">Requirements</span></span>  
 <span data-ttu-id="a493f-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a493f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a493f-123">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a493f-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a493f-124">**Biblioteca:** mscoree. dll e o arquivo Mscorwks.dll.</span><span class="sxs-lookup"><span data-stu-id="a493f-124">**Library:** MSCorEE.dll and Mscorwks.dll.</span></span> <span data-ttu-id="a493f-125">Use mscoree em vez do arquivo Mscorwks.dll para garantir que você a versão correta do .NET Framework de destino.</span><span class="sxs-lookup"><span data-stu-id="a493f-125">Use MSCorEE.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="a493f-126">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a493f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a493f-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a493f-127">See Also</span></span>  
 [<span data-ttu-id="a493f-128">Função LoadStringRCEx</span><span class="sxs-lookup"><span data-stu-id="a493f-128">LoadStringRCEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)  
 [<span data-ttu-id="a493f-129">Funções de hospedagem CLR reprovadas</span><span class="sxs-lookup"><span data-stu-id="a493f-129">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
