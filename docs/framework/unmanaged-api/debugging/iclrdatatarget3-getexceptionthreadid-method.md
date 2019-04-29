---
title: ICLRDataTarget3::Método GetExceptionThreadID
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6503efbaa4db89b243a85b69f60b091c6bb49ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697895"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="8ad6b-102">ICLRDataTarget3::Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="8ad6b-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="8ad6b-103">Chamado pelos serviços de acesso a dados do CLR (Common Language Runtime) para obter a ID do segmento que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="8ad6b-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad6b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ad6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad6b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ad6b-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="8ad6b-106">[out] A ID do thread que acionou a exceção.</span><span class="sxs-lookup"><span data-stu-id="8ad6b-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ad6b-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="8ad6b-107">Return Value</span></span>  
 <span data-ttu-id="8ad6b-108">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="8ad6b-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="8ad6b-109">Os códigos `HRESULT` podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="8ad6b-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="8ad6b-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="8ad6b-110">Return code</span></span>|<span data-ttu-id="8ad6b-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="8ad6b-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="8ad6b-112">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="8ad6b-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="8ad6b-113">Não foi possível encontrar uma ID de thread válida para a exceção.</span><span class="sxs-lookup"><span data-stu-id="8ad6b-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8ad6b-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ad6b-114">Remarks</span></span>  
 <span data-ttu-id="8ad6b-115">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="8ad6b-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad6b-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8ad6b-116">Requirements</span></span>  
 <span data-ttu-id="8ad6b-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ad6b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ad6b-118">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="8ad6b-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8ad6b-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8ad6b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8ad6b-120">**Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8ad6b-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad6b-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ad6b-121">See also</span></span>

- [<span data-ttu-id="8ad6b-122">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="8ad6b-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="8ad6b-123">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="8ad6b-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="8ad6b-124">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="8ad6b-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
