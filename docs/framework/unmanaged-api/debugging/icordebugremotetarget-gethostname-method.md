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
ms.openlocfilehash: f177d441da3bd967750781e487d9fed42bc132f5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791941"
---
# <a name="icordebugremotetargetgethostname-method"></a><span data-ttu-id="22861-102">Método ICorDebugRemoteTarget::GetHostName</span><span class="sxs-lookup"><span data-stu-id="22861-102">ICorDebugRemoteTarget::GetHostName Method</span></span>
<span data-ttu-id="22861-103">Retorna o nome de domínio totalmente qualificado ou o endereço IPv4 do computador de destino de depuração remota.</span><span class="sxs-lookup"><span data-stu-id="22861-103">Returns the fully qualified domain name or IPv4 address of the remote debugging target machine.</span></span> <span data-ttu-id="22861-104">Não há suporte para IPV6 no momento.</span><span class="sxs-lookup"><span data-stu-id="22861-104">IPV6 is not supported at this time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22861-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22861-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHostName (  
    [in] ULONG32      cchHostName,  
    [out] ULONG32*    pcchHostName,  
    [out, size_is(cchHostName), length_is(*pcchHostName)]  
            WCHAR szHostName[]  
```  
  
## <a name="parameters"></a><span data-ttu-id="22861-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="22861-106">Parameters</span></span>  
 `cchHostName`  
 <span data-ttu-id="22861-107">no O tamanho, em caracteres, do buffer de `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="22861-107">[in] The size, in characters, of the `szHostName` buffer.</span></span> <span data-ttu-id="22861-108">Se esse parâmetro for 0 (zero), `szHostName` deverá ser NULL.</span><span class="sxs-lookup"><span data-stu-id="22861-108">If this parameter is 0 (zero), `szHostName` must be null.</span></span>  
  
 `pcchHostName`  
 <span data-ttu-id="22861-109">fora O número de caracteres, incluindo um terminador nulo, no nome do host ou endereço IP.</span><span class="sxs-lookup"><span data-stu-id="22861-109">[out] The number of characters, including a null terminator, in the host name or IP address.</span></span> <span data-ttu-id="22861-110">Este parâmetro pode ser nulo.</span><span class="sxs-lookup"><span data-stu-id="22861-110">This parameter can be null.</span></span>  
  
 `szHostName`  
 <span data-ttu-id="22861-111">fora Buffer que contém o nome do host ou o endereço IP.</span><span class="sxs-lookup"><span data-stu-id="22861-111">[out] Buffer that contains the host name or IP address.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22861-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="22861-112">Return Value</span></span>  
 <span data-ttu-id="22861-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="22861-113">S_OK</span></span>  
 <span data-ttu-id="22861-114">O nome do host ou o endereço IP foi retornado com êxito.</span><span class="sxs-lookup"><span data-stu-id="22861-114">The host name or IP address was successfully returned.</span></span>  
  
 <span data-ttu-id="22861-115">E_FAIL (ou outros códigos de retorno de E_)</span><span class="sxs-lookup"><span data-stu-id="22861-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="22861-116">Não é possível retornar o nome do host ou o endereço IP.</span><span class="sxs-lookup"><span data-stu-id="22861-116">Unable to return the host name or IP address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22861-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="22861-117">Remarks</span></span>  
 <span data-ttu-id="22861-118">Esse método é implementado pelo gravador do depurador.</span><span class="sxs-lookup"><span data-stu-id="22861-118">This method is implemented by the debugger writer.</span></span> <span data-ttu-id="22861-119">Ele deve seguir o paradigma de chamada múltipla: na primeira chamada, o chamador passa nulo para `cchHostName` e `szHostName`e `pcchHostName` retorna o tamanho do buffer necessário.</span><span class="sxs-lookup"><span data-stu-id="22861-119">It must follow the multiple call paradigm: On the first call, the caller passes null to both `cchHostName` and `szHostName`, and `pcchHostName` returns the size of the required buffer.</span></span> <span data-ttu-id="22861-120">Na segunda chamada, o tamanho retornado anteriormente é passado em `cchHostName`e um buffer de tamanho apropriado é passado `szHostName`.</span><span class="sxs-lookup"><span data-stu-id="22861-120">On the second call, the size that was previously returned is passed in `cchHostName`, and an appropriately sized buffer is passed in `szHostName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22861-121">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="22861-121">Requirements</span></span>  
 <span data-ttu-id="22861-122">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22861-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22861-123">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="22861-123">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="22861-124">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22861-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22861-125">**Versões do .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="22861-125">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22861-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="22861-126">See also</span></span>

- [<span data-ttu-id="22861-127">Interface ICorDebugRemoteTarget</span><span class="sxs-lookup"><span data-stu-id="22861-127">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="22861-128">Interface ICorDebug</span><span class="sxs-lookup"><span data-stu-id="22861-128">ICorDebug Interface</span></span>](icordebug-interface.md)
