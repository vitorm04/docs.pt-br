---
title: "Método ISymUnmanagedReader::Initialize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 433cd62f7801d386f3b34b7fc8e95bd1d0c5f765
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="48e0f-102">Método ISymUnmanagedReader::Initialize</span><span class="sxs-lookup"><span data-stu-id="48e0f-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="48e0f-103">Inicializa o leitor de símbolo com a interface de Importador de metadados que este leitor será associado, juntamente com o nome de arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="48e0f-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48e0f-104">Esse método pode ser chamado apenas uma vez e deve ser chamado antes de quaisquer outros métodos de leitor.</span><span class="sxs-lookup"><span data-stu-id="48e0f-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48e0f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48e0f-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="48e0f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="48e0f-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="48e0f-107">[in] A interface de Importador de metadados com a qual este leitor será associado.</span><span class="sxs-lookup"><span data-stu-id="48e0f-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="48e0f-108">[in] O nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="48e0f-108">[in] The file name of the module.</span></span> <span data-ttu-id="48e0f-109">Você pode usar o `pIStream` parâmetro em vez disso.</span><span class="sxs-lookup"><span data-stu-id="48e0f-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="48e0f-110">[in] Caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="48e0f-110">[in] The path to search.</span></span> <span data-ttu-id="48e0f-111">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="48e0f-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="48e0f-112">[in] O fluxo de arquivos, usado como uma alternativa para o parâmetro de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="48e0f-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="48e0f-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="48e0f-113">Return Value</span></span>  
 <span data-ttu-id="48e0f-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="48e0f-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48e0f-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="48e0f-115">Remarks</span></span>  
 <span data-ttu-id="48e0f-116">Você precisa especificar apenas um o `filename` ou `pIStream` parâmetros, não ambos.</span><span class="sxs-lookup"><span data-stu-id="48e0f-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="48e0f-117">O parâmetro `searchPath` é opcional.</span><span class="sxs-lookup"><span data-stu-id="48e0f-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48e0f-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48e0f-118">Requirements</span></span>  
 <span data-ttu-id="48e0f-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="48e0f-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e0f-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48e0f-120">See Also</span></span>  
 [<span data-ttu-id="48e0f-121">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="48e0f-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
