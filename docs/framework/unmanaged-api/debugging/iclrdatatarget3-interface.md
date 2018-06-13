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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54d6535e2b2c4761eb3c67a990c62f2c311cf133
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406858"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="41e2c-102">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="41e2c-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="41e2c-103">Uma subclasse de [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) que fornece acesso às informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="41e2c-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41e2c-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="41e2c-104">Methods</span></span>  
  
|<span data-ttu-id="41e2c-105">Método</span><span class="sxs-lookup"><span data-stu-id="41e2c-105">Method</span></span>|<span data-ttu-id="41e2c-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="41e2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41e2c-107">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="41e2c-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="41e2c-108">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="41e2c-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="41e2c-109">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="41e2c-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="41e2c-110">Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="41e2c-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="41e2c-111">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="41e2c-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="41e2c-112">Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.</span><span class="sxs-lookup"><span data-stu-id="41e2c-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41e2c-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="41e2c-113">Remarks</span></span>  
 <span data-ttu-id="41e2c-114">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="41e2c-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="41e2c-115">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="41e2c-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="41e2c-116">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="41e2c-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41e2c-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="41e2c-117">Requirements</span></span>  
 <span data-ttu-id="41e2c-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41e2c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41e2c-119">**Cabeçalho:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="41e2c-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="41e2c-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41e2c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41e2c-121">**Versões do .NET framework:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41e2c-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e2c-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41e2c-122">See Also</span></span>  
 [<span data-ttu-id="41e2c-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="41e2c-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="41e2c-124">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="41e2c-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="41e2c-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="41e2c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
