---
title: Interface ICLRDataTarget3
ms.date: 03/30/2017
api_name:
- ICLRDataTarget3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type:
- apiref
ms.openlocfilehash: a6591f7d7b632bcdbdabb1633f7431d79da7ff6e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73111823"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="9ed13-102">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="9ed13-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="9ed13-103">Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="9ed13-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9ed13-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9ed13-104">Methods</span></span>  
  
|<span data-ttu-id="9ed13-105">Método</span><span class="sxs-lookup"><span data-stu-id="9ed13-105">Method</span></span>|<span data-ttu-id="9ed13-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="9ed13-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ed13-107">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="9ed13-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="9ed13-108">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="9ed13-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="9ed13-109">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="9ed13-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="9ed13-110">Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="9ed13-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="9ed13-111">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="9ed13-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="9ed13-112">Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.</span><span class="sxs-lookup"><span data-stu-id="9ed13-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed13-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="9ed13-113">Remarks</span></span>  
 <span data-ttu-id="9ed13-114">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="9ed13-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="9ed13-115">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="9ed13-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="9ed13-116">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="9ed13-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed13-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9ed13-117">Requirements</span></span>  
 <span data-ttu-id="9ed13-118">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed13-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed13-119">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9ed13-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9ed13-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ed13-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ed13-121">**Versões do .NET Framework:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed13-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed13-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9ed13-122">See also</span></span>

- [<span data-ttu-id="9ed13-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="9ed13-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
- [<span data-ttu-id="9ed13-124">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="9ed13-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)
- [<span data-ttu-id="9ed13-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="9ed13-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
