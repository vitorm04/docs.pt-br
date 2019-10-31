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
ms.openlocfilehash: 8541e7761e2f8e1839d028fdaea3eb71307ba615
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131194"
---
# <a name="_corexemain-function"></a><span data-ttu-id="90792-102">Função _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="90792-102">_CorExeMain Function</span></span>
<span data-ttu-id="90792-103">Inicializa o Common Language Runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="90792-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90792-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90792-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="90792-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="90792-105">Remarks</span></span>  
 <span data-ttu-id="90792-106">Essa função é chamada pelo carregador em processos criados a partir de assemblies executáveis gerenciados.</span><span class="sxs-lookup"><span data-stu-id="90792-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="90792-107">Para assemblies DLL, o carregador chama a função [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="90792-107">For DLL assemblies, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="90792-108">O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="90792-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="90792-109">No Windows 98, Windows ME, Windows NT e Windows 2000, a função `_CorExeMain` é chamada indiretamente por meio de uma correção no carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="90792-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="90792-110">Em todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="90792-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="90792-111">Para obter informações adicionais, consulte a seção comentários no tópico [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="90792-111">For additional information, see the Remarks section in the [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90792-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90792-112">Requirements</span></span>  
 <span data-ttu-id="90792-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90792-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90792-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="90792-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="90792-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="90792-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="90792-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90792-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90792-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90792-117">See also</span></span>

- [<span data-ttu-id="90792-118">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="90792-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
