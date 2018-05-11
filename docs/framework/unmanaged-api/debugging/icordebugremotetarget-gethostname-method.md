---
title: Método ICorDebugRemoteTarget::GetHostName
ms.date: 03/30/2017
api_name:
- ICorDebugRemoteTarget.GetHostName
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::GetHostName
helpviewer_keywords:
- ICorDebugRemoteTarget::GetHostName method [.NET Framework debugging]
- GetHostName method, ICorDebugRemoteTarget interface [.NET Framework debugging]
ms.assetid: 1c7276f7-7e54-470c-808c-e13745ac07a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1536a89d0e85480d3829939c40cd986fe65883df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="5268d-102">Método ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="5268d-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="5268d-103">Retorna o nome de domínio totalmente qualificado ou o endereço IPv4 do computador de destino de depuração remota.</span><span class="sxs-lookup"><span data-stu-id="5268d-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="5268d-104">Não há suporte para IPv6 neste momento.</span><span class="sxs-lookup"><span data-stu-id="5268d-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5268d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5268d-105">Syntax</span></span>  
  
```  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5268d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="5268d-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="5268d-107">[in] O tamanho, em caracteres, do `szHostName` buffer.</span><span class="sxs-lookup"><span data-stu-id="5268d-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="5268d-108">Se esse parâmetro for 0 (zero), `szHostName` deve ser nulo.</span><span class="sxs-lookup"><span data-stu-id="5268d-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="5268d-109">[out] O número de caracteres, incluindo um terminador nulo, o nome do host ou endereço IP.</span><span class="sxs-lookup"><span data-stu-id="5268d-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="5268d-110">Este parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="5268d-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="5268d-111">[out] Buffer que contém o nome do host ou endereço IP.</span><span class="sxs-lookup"><span data-stu-id="5268d-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5268d-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="5268d-112">Return Value</span></span>  
 <span data-ttu-id="5268d-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="5268d-113">S_OK</span></span>  
 <span data-ttu-id="5268d-114">O nome do host ou endereço IP foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="5268d-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="5268d-115">E_FAIL (ou outros códigos de retorno E_)</span><span class="sxs-lookup"><span data-stu-id="5268d-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="5268d-116">Não é possível retornar o nome de host ou endereço IP.</span><span class="sxs-lookup"><span data-stu-id="5268d-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5268d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="5268d-117">Remarks</span></span>  
 <span data-ttu-id="5268d-118">Esse método é implementado pelo gerador de depurador.</span><span class="sxs-lookup"><span data-stu-id="5268d-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="5268d-119">Ele deve seguir o paradigma de chamada vários: na primeira chamada, o chamador passa nulo para ambos `cchHostName` e `szHostName`, e `pcchHostName` retorna o tamanho do buffer necessário.</span><span class="sxs-lookup"><span data-stu-id="5268d-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer .</span></span> <span data-ttu-id="5268d-120">Na segunda chamada, o tamanho que anteriormente era retornado é passado `cchHostName`, e um buffer de tamanho apropriado é passado no `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="5268d-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5268d-121">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5268d-121">Requirements</span></span>  
 <span data-ttu-id="5268d-122">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5268d-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5268d-123">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="5268d-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="5268d-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5268d-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5268d-125">**Versões do .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="5268d-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5268d-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5268d-126">See Also</span></span>  
 [<span data-ttu-id="5268d-127">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="5268d-127">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="5268d-128">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="5268d-128">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
