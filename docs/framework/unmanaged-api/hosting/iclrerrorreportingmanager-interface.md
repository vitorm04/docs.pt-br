---
title: Interface ICLRErrorReportingManager
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: dbe4129cf4160a1a9b31bc6f418095ea4b392d57
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616990"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="e4101-102">Interface ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="e4101-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="e4101-103">Fornece métodos que permitem ao host configurar despejos de pilha personalizados para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="e4101-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e4101-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="e4101-104">Methods</span></span>  
  
|<span data-ttu-id="e4101-105">Método</span><span class="sxs-lookup"><span data-stu-id="e4101-105">Method</span></span>|<span data-ttu-id="e4101-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="e4101-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e4101-107">Método BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="e4101-107">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="e4101-108">Especifica a configuração de despejos de pilha personalizados para o relatório de erros.</span><span class="sxs-lookup"><span data-stu-id="e4101-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="e4101-109">Método EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="e4101-109">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="e4101-110">Limpa a configuração de despejo de pilha personalizado que foi definida por uma chamada anterior para `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="e4101-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="e4101-111">Método GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="e4101-111">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="e4101-112">Obtém o Bucket do Watson para a exceção atual no thread de chamada.</span><span class="sxs-lookup"><span data-stu-id="e4101-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4101-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="e4101-113">Remarks</span></span>  
 <span data-ttu-id="e4101-114">O `BeginCustomDump` método define a configuração de despejo de pilha personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4101-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="e4101-115">O `EndCustomDump` método limpa a configuração de despejo de pilha personalizada e libera qualquer estado associado.</span><span class="sxs-lookup"><span data-stu-id="e4101-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="e4101-116">Ele deve ser chamado após a conclusão do despejo personalizado.</span><span class="sxs-lookup"><span data-stu-id="e4101-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="e4101-117">Falha ao chamar `EndCustomDump` faz com que a memória seja vazada.</span><span class="sxs-lookup"><span data-stu-id="e4101-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4101-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e4101-118">Requirements</span></span>  
 <span data-ttu-id="e4101-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4101-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4101-120">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e4101-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e4101-121">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e4101-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e4101-122">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4101-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4101-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="e4101-123">See also</span></span>

- [<span data-ttu-id="e4101-124">Enumeração ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="e4101-124">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="e4101-125">Interfaces de hospedagem</span><span class="sxs-lookup"><span data-stu-id="e4101-125">Hosting Interfaces</span></span>](hosting-interfaces.md)
