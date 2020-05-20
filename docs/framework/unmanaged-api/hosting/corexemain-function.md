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
ms.openlocfilehash: 935ac478fb966315e81fdcc004761038b28e3178
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616581"
---
# <a name="_corexemain-function"></a><span data-ttu-id="b6f94-102">Função _CorExeMain</span><span class="sxs-lookup"><span data-stu-id="b6f94-102">_CorExeMain Function</span></span>
<span data-ttu-id="b6f94-103">Inicializa o Common Language Runtime (CLR), localiza o ponto de entrada gerenciado no cabeçalho CLR do assembly executável e começa a execução.</span><span class="sxs-lookup"><span data-stu-id="b6f94-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6f94-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6f94-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="b6f94-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6f94-105">Remarks</span></span>  
 <span data-ttu-id="b6f94-106">Essa função é chamada pelo carregador em processos criados a partir de assemblies executáveis gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b6f94-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="b6f94-107">Para assemblies DLL, o carregador chama a função [_CorDllMain](cordllmain-function.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b6f94-107">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="b6f94-108">O carregador do sistema operacional chama esse método, independentemente do ponto de entrada especificado no arquivo de imagem.</span><span class="sxs-lookup"><span data-stu-id="b6f94-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="b6f94-109">No Windows 98, Windows ME, Windows NT e Windows 2000, a `_CorExeMain` função é chamada indiretamente por meio de uma correção no carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b6f94-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="b6f94-110">Em todas as outras versões do Windows, ele é chamado diretamente pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="b6f94-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="b6f94-111">Para obter informações adicionais, consulte a seção comentários no tópico [_CorValidateImage](corvalidateimage-function.md) .</span><span class="sxs-lookup"><span data-stu-id="b6f94-111">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6f94-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b6f94-112">Requirements</span></span>  
 <span data-ttu-id="b6f94-113">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6f94-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6f94-114">**Cabeçalho:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b6f94-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6f94-115">**Biblioteca:** Incluído como um recurso em MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6f94-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6f94-116">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6f94-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6f94-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6f94-117">See also</span></span>

- [<span data-ttu-id="b6f94-118">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="b6f94-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
