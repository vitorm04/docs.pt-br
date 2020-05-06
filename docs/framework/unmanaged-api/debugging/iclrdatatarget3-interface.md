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
ms.openlocfilehash: af944a9c2bb04f37b06f27cfbe38e23c9613d768
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860408"
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="4804d-102">Interface ICLRDataTarget3</span><span class="sxs-lookup"><span data-stu-id="4804d-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="4804d-103">Uma subclasse de [ICLRDataTarget2](iclrdatatarget2-interface.md) que fornece acesso a informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="4804d-103">A subclass of [ICLRDataTarget2](iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4804d-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="4804d-104">Methods</span></span>  
  
|<span data-ttu-id="4804d-105">Método</span><span class="sxs-lookup"><span data-stu-id="4804d-105">Method</span></span>|<span data-ttu-id="4804d-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="4804d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4804d-107">Método GetExceptionRecord</span><span class="sxs-lookup"><span data-stu-id="4804d-107">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="4804d-108">Chamado pelo serviço de acesso a dados do CLR (Common Language Runtime) para recuperar o registro de exceção associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4804d-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="4804d-109">Método GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="4804d-109">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="4804d-110">Chamado pelo serviço de acesso a dados do CLR para recuperar o registro de contexto associado ao processo de destino.</span><span class="sxs-lookup"><span data-stu-id="4804d-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="4804d-111">Método GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="4804d-111">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="4804d-112">Chamado pelos serviços de acesso a dados do CLR para obter o ID do thread que lança a exceção.</span><span class="sxs-lookup"><span data-stu-id="4804d-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4804d-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="4804d-113">Remarks</span></span>  
 <span data-ttu-id="4804d-114">O cliente da API (ou seja, o depurador) deve implementar a interface conforme o apropriado para o processo de destino específico.</span><span class="sxs-lookup"><span data-stu-id="4804d-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="4804d-115">Por exemplo, um processo dinâmico teria uma implementação diferente da implementação de um despejo de memória.</span><span class="sxs-lookup"><span data-stu-id="4804d-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="4804d-116">O destino pode não oferecer suporte à modificação de suas regiões de memória.</span><span class="sxs-lookup"><span data-stu-id="4804d-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4804d-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4804d-117">Requirements</span></span>  
 <span data-ttu-id="4804d-118">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4804d-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4804d-119">**Cabeçalho:** ClrData. idl, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="4804d-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="4804d-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4804d-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4804d-121">**.NET Framework versões:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="4804d-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4804d-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="4804d-122">See also</span></span>

- [<span data-ttu-id="4804d-123">Interface ICLRDataTarget</span><span class="sxs-lookup"><span data-stu-id="4804d-123">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
- [<span data-ttu-id="4804d-124">Interface ICLRDataTarget2</span><span class="sxs-lookup"><span data-stu-id="4804d-124">ICLRDataTarget2 Interface</span></span>](iclrdatatarget2-interface.md)
- [<span data-ttu-id="4804d-125">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="4804d-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
