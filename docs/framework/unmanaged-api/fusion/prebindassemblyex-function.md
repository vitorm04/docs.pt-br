---
title: Função PreBindAssemblyEx
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8251d21fe535f85cc6abd0a7bc6c96ab320007f0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090232"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="bbdc2-102">Função PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="bbdc2-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="bbdc2-103">Obtém o nome de exibição de pós-política para um assembly.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="bbdc2-104">Essa função dá suporte à infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbdc2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbdc2-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="bbdc2-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbdc2-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="bbdc2-107">[in] Identifica o contexto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="bbdc2-108">[in] Identifica o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="bbdc2-109">[in] Identifica o assembly pai.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="bbdc2-110">Este parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="bbdc2-111">[in] Identifica a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="bbdc2-112">[out] Contém o nome de exibição de pós política de.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="bbdc2-113">[in] Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-113">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="bbdc2-114">deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-114">must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbdc2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="bbdc2-115">Remarks</span></span>  
 <span data-ttu-id="bbdc2-116">O `ppNamePostPolicy` parâmetro de saída será definido somente se a função retorna FUSION_E_REF_DEF_MISMATCH HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="bbdc2-117">Caso contrário, será nulo.</span><span class="sxs-lookup"><span data-stu-id="bbdc2-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbdc2-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbdc2-118">Requirements</span></span>  
 <span data-ttu-id="bbdc2-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbdc2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbdc2-120">**Cabeçalho:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="bbdc2-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bbdc2-121">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="bbdc2-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bbdc2-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="bbdc2-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bbdc2-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbdc2-123">See also</span></span>

- [<span data-ttu-id="bbdc2-124">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="bbdc2-124">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
