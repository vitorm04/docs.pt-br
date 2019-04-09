---
title: Função _CorExeMain
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7407db297a827004c851b904b2da8652778cb08
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177483"
---
# <a name="corexemain-function"></a><span data-ttu-id="44b9f-102">Função _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="44b9f-102">_CorExeMain Function</span></span>
<span data-ttu-id="44b9f-103">Inicializa o common language runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e inicia a execução.</span><span class="sxs-lookup"><span data-stu-id="44b9f-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44b9f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44b9f-104">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="44b9f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="44b9f-105">Remarks</span></span>  
 <span data-ttu-id="44b9f-106">Essa função é chamada pelo carregador em processos criados a partir de assemblies executáveis gerenciados.</span><span class="sxs-lookup"><span data-stu-id="44b9f-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="44b9f-107">Para assemblies DLL, o carregador de chamadas a [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function em vez disso.</span><span class="sxs-lookup"><span data-stu-id="44b9f-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="44b9f-108">Carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="44b9f-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="44b9f-109">No Windows 98, Windows ME, Windows NT e Windows 2000, o `_CorExeMain` função é chamada indiretamente por meio de uma correção no carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="44b9f-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="44b9f-110">Todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="44b9f-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="44b9f-111">Para obter mais informações, consulte a seção comentários a [CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="44b9f-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44b9f-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="44b9f-112">Requirements</span></span>  
 <span data-ttu-id="44b9f-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44b9f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44b9f-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="44b9f-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="44b9f-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="44b9f-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="44b9f-116">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="44b9f-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="44b9f-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44b9f-117">See also</span></span>

- [<span data-ttu-id="44b9f-118">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="44b9f-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
