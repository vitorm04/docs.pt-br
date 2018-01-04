---
title: "Função PreBindAssemblyEx"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: PreBindAssemblyEx
api_location: fusion.dll
api_type: DLLExport
f1_keywords: PreBindAssemblyEx
helpviewer_keywords: PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 05977db8e01d00af6e160cb2993867cf83eb24c1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="db29e-102">Função PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="db29e-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="db29e-103">Obtém o nome de exibição de pós-política para um assembly.</span><span class="sxs-lookup"><span data-stu-id="db29e-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="db29e-104">Essa função dá suporte à infraestrutura .NET Framework e não se destina a ser usado diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="db29e-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db29e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="db29e-105">Syntax</span></span>  
  
```  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db29e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="db29e-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="db29e-107">[in] Identifica o contexto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="db29e-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="db29e-108">[in] Identifica o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="db29e-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="db29e-109">[in] Identifica o assembly pai.</span><span class="sxs-lookup"><span data-stu-id="db29e-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="db29e-110">Este parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="db29e-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="db29e-111">[in] Identifica a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="db29e-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="db29e-112">[out] Contém o nome de exibição de pós política de.</span><span class="sxs-lookup"><span data-stu-id="db29e-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="db29e-113">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="db29e-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="db29e-114">`pvReserved`deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="db29e-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db29e-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="db29e-115">Remarks</span></span>  
 <span data-ttu-id="db29e-116">O `ppNamePostPolicy` parâmetro de saída é definido somente se a função retorna um HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="db29e-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="db29e-117">Caso contrário, será nulo.</span><span class="sxs-lookup"><span data-stu-id="db29e-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db29e-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="db29e-118">Requirements</span></span>  
 <span data-ttu-id="db29e-119">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db29e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db29e-120">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="db29e-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="db29e-121">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="db29e-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="db29e-122">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db29e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db29e-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="db29e-123">See Also</span></span>  
 [<span data-ttu-id="db29e-124">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="db29e-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
