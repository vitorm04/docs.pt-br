---
title: "Função _CorExeMain"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5f5c0909db10c7bf8e15a7af998b78e0a193a908
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="corexemain-function"></a><span data-ttu-id="cd6fa-102">Função _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="cd6fa-102">_CorExeMain Function</span></span>
<span data-ttu-id="cd6fa-103">Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho do executável do assembly CLR e começa a ser executada.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd6fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd6fa-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd6fa-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd6fa-105">Remarks</span></span>  
 <span data-ttu-id="cd6fa-106">Essa função é chamada pelo carregador em processos criado a partir de assemblies gerenciados de executável.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="cd6fa-107">Para os assemblies DLL, chama o carregador de [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="cd6fa-108">O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="cd6fa-109">No Windows 98, Windows ME, Windows NT e Windows 2000, o `_CorExeMain` função é chamada indiretamente por meio de um ajuste no carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="cd6fa-110">Em todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="cd6fa-111">Para obter mais informações, consulte a seção comentários a [CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="cd6fa-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd6fa-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cd6fa-112">Requirements</span></span>  
 <span data-ttu-id="cd6fa-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd6fa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd6fa-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="cd6fa-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd6fa-115">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="cd6fa-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd6fa-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd6fa-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd6fa-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd6fa-117">See Also</span></span>  
 [<span data-ttu-id="cd6fa-118">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="cd6fa-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
