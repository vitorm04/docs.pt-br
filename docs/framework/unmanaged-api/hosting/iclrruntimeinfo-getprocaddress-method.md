---
title: Método ICLRRuntimeInfo::GetProcAddress
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.GetProcAddress
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::GetProcAddress
helpviewer_keywords:
- GetProcAddress method [.NET Framework hosting]
- ICLRRuntimeInfo::GetProcAddress method [.NET Framework hosting]
ms.assetid: a7732bfc-689a-4926-88fd-4f81e6f9ed78
topic_type:
- apiref
ms.openlocfilehash: 2690a5c2e7c499d68ef9e903c62bff8f85e72e8e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703873"
---
# <a name="iclrruntimeinfogetprocaddress-method"></a><span data-ttu-id="29046-102">Método ICLRRuntimeInfo::GetProcAddress</span><span class="sxs-lookup"><span data-stu-id="29046-102">ICLRRuntimeInfo::GetProcAddress Method</span></span>
<span data-ttu-id="29046-103">Obtém o endereço de uma função especificada que foi exportada do Common Language Runtime (CLR) associado a esta interface.</span><span class="sxs-lookup"><span data-stu-id="29046-103">Gets the address of a specified function that was exported from the common language runtime (CLR) associated with this interface.</span></span>  
  
 <span data-ttu-id="29046-104">Esse método substitui a função [GetRealProcAddress](getrealprocaddress-function.md) .</span><span class="sxs-lookup"><span data-stu-id="29046-104">This method supersedes the [GetRealProcAddress](getrealprocaddress-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29046-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29046-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcAddress(  
     [in]  LPCSTR pszProcName,  
     [out, retval] LPVOID *ppProc);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29046-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29046-106">Parameters</span></span>  
 `pszProcName`  
 <span data-ttu-id="29046-107">no O nome da função exportada.</span><span class="sxs-lookup"><span data-stu-id="29046-107">[in] The name of the exported function.</span></span>  
  
 `ppProc`  
 <span data-ttu-id="29046-108">fora O endereço da função exportada.</span><span class="sxs-lookup"><span data-stu-id="29046-108">[out] The address of the exported function.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29046-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="29046-109">Return Value</span></span>  
 <span data-ttu-id="29046-110">Esse método retorna os HRESULTs específicos a seguir, bem como os erros de HRESULT que indicam falha de método.</span><span class="sxs-lookup"><span data-stu-id="29046-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="29046-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="29046-111">HRESULT</span></span>|<span data-ttu-id="29046-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="29046-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="29046-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="29046-113">S_OK</span></span>|<span data-ttu-id="29046-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="29046-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="29046-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="29046-115">E_POINTER</span></span>|<span data-ttu-id="29046-116">`pszProcName` ou `ppProc` é nulo.</span><span class="sxs-lookup"><span data-stu-id="29046-116">`pszProcName` or `ppProc` is null.</span></span>|  
|<span data-ttu-id="29046-117">CLR_E_SHIM_RUNTIMEEXPORT</span><span class="sxs-lookup"><span data-stu-id="29046-117">CLR_E_SHIM_RUNTIMEEXPORT</span></span>|<span data-ttu-id="29046-118">A função especificada não é uma função exportada.</span><span class="sxs-lookup"><span data-stu-id="29046-118">The specified function is not an exported function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29046-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="29046-119">Remarks</span></span>  
 <span data-ttu-id="29046-120">Esse método faz com que o CLR seja carregado, mas não inicializado.</span><span class="sxs-lookup"><span data-stu-id="29046-120">This method causes the CLR to be loaded but not initialized.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29046-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29046-121">Requirements</span></span>  
 <span data-ttu-id="29046-122">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29046-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29046-123">**Cabeçalho:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="29046-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="29046-124">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="29046-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="29046-125">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29046-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29046-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="29046-126">See also</span></span>

- [<span data-ttu-id="29046-127">Interface ICLRRuntimeInfo</span><span class="sxs-lookup"><span data-stu-id="29046-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="29046-128">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="29046-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="29046-129">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="29046-129">Hosting</span></span>](index.md)
