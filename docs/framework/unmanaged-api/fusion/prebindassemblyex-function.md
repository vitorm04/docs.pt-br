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
ms.openlocfilehash: db3ba3380d1fc30a8f34683618b5cc326d7d1906
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123052"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="5ccbe-102">Função PreBindAssemblyEx</span><span class="sxs-lookup"><span data-stu-id="5ccbe-102">PreBindAssemblyEx Function</span></span>
<span data-ttu-id="5ccbe-103">Obtém o nome de exibição de pós-política para um assembly.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="5ccbe-104">Essa função dá suporte à infraestrutura de .NET Framework e não se destina a ser usada diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ccbe-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ccbe-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ccbe-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5ccbe-106">Parameters</span></span>  
 `pAppCtx`  
 <span data-ttu-id="5ccbe-107">no Identifica o contexto do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="5ccbe-108">no Identifica o nome do assembly.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="5ccbe-109">no Identifica o assembly pai.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="5ccbe-110">Este parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="5ccbe-111">no Identifica a versão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="5ccbe-112">fora Contém o nome de exibição de pós-política.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="5ccbe-113">no Reservado para extensibilidade futura.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="5ccbe-114">`pvReserved` deve ser uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ccbe-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ccbe-115">Remarks</span></span>  
 <span data-ttu-id="5ccbe-116">O parâmetro de saída `ppNamePostPolicy` será definido somente se a função retornar HRESULT FUSION_E_REF_DEF_MISMATCH.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="5ccbe-117">Caso contrário, será nulo.</span><span class="sxs-lookup"><span data-stu-id="5ccbe-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ccbe-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5ccbe-118">Requirements</span></span>  
 <span data-ttu-id="5ccbe-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ccbe-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ccbe-120">**Cabeçalho:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="5ccbe-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5ccbe-121">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5ccbe-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5ccbe-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ccbe-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ccbe-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ccbe-123">See also</span></span>

- [<span data-ttu-id="5ccbe-124">Funções estáticas globais de fusão</span><span class="sxs-lookup"><span data-stu-id="5ccbe-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
