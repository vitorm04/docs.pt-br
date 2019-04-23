---
title: Função _CorExeMain2
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f968d84ae695eb1da127538ebdc5e4f55d6ebf39
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183151"
---
# <a name="corexemain2-function"></a><span data-ttu-id="2236e-102">Função _CorExeMain2</span><span class="sxs-lookup"><span data-stu-id="2236e-102">_CorExeMain2 Function</span></span>
<span data-ttu-id="2236e-103">Executa o ponto de entrada no código mapeado na memória especificado.</span><span class="sxs-lookup"><span data-stu-id="2236e-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="2236e-104">Essa função é chamada pelo carregador do sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="2236e-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2236e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2236e-105">Syntax</span></span>  
  
```  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2236e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2236e-106">Parameters</span></span>  
 `pUnmappedPE`  
 <span data-ttu-id="2236e-107">[in] Um ponteiro para o código mapeado na memória.</span><span class="sxs-lookup"><span data-stu-id="2236e-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="2236e-108">[in] O número de elementos `pUnmappedPE` pode conter.</span><span class="sxs-lookup"><span data-stu-id="2236e-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="2236e-109">[in] Um ponteiro para o nome da imagem executável.</span><span class="sxs-lookup"><span data-stu-id="2236e-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="2236e-110">[in] O nome do arquivo de carregador.</span><span class="sxs-lookup"><span data-stu-id="2236e-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="2236e-111">[in] Parâmetros de linha de comando, se houver.</span><span class="sxs-lookup"><span data-stu-id="2236e-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2236e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2236e-112">Requirements</span></span>  
 <span data-ttu-id="2236e-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2236e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2236e-114">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2236e-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2236e-115">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="2236e-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2236e-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2236e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2236e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2236e-117">See also</span></span>

- [<span data-ttu-id="2236e-118">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="2236e-118">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
