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
ms.openlocfilehash: 63c92e3f34527f895552f45d43f332f778470b13
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860428"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="c2d94-102">ICLRDataTarget3::Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="c2d94-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="c2d94-103">Chamado pelos serviços de acesso a dados do CLR (Common Language Runtime) para obter a ID do segmento que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="c2d94-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c2d94-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2d94-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c2d94-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c2d94-106">[out] A ID do thread que acionou a exceção.</span><span class="sxs-lookup"><span data-stu-id="c2d94-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2d94-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c2d94-107">Return Value</span></span>  
 <span data-ttu-id="c2d94-108">O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha.</span><span class="sxs-lookup"><span data-stu-id="c2d94-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="c2d94-109">Os códigos `HRESULT` podem incluir, entre outros:</span><span class="sxs-lookup"><span data-stu-id="c2d94-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="c2d94-110">Código de retorno</span><span class="sxs-lookup"><span data-stu-id="c2d94-110">Return code</span></span>|<span data-ttu-id="c2d94-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="c2d94-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="c2d94-112">O método foi bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="c2d94-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="c2d94-113">Não foi possível encontrar uma ID de thread válida para a exceção.</span><span class="sxs-lookup"><span data-stu-id="c2d94-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2d94-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="c2d94-114">Remarks</span></span>  
 <span data-ttu-id="c2d94-115">Este método é implementado pelo autor do aplicativo de depuração.</span><span class="sxs-lookup"><span data-stu-id="c2d94-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d94-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c2d94-116">Requirements</span></span>  
 <span data-ttu-id="c2d94-117">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d94-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d94-118">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c2d94-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c2d94-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2d94-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2d94-120">**.NET Framework versões:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c2d94-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d94-121">Confira também</span><span class="sxs-lookup"><span data-stu-id="c2d94-121">See also</span></span>

- [<span data-ttu-id="c2d94-122">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="c2d94-122">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="c2d94-123">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="c2d94-123">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="c2d94-124">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="c2d94-124">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
