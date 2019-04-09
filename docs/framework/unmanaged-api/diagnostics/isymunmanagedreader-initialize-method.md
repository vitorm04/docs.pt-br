---
title: Método ISymUnmanagedReader::Initialize
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 661c27b9c21f77104b8a86163d3c92d44f8a85df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181773"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="c1c75-102">Método ISymUnmanagedReader::Initialize</span><span class="sxs-lookup"><span data-stu-id="c1c75-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="c1c75-103">Inicializa o leitor de símbolo com a interface do importador de metadados que esse leitor será associado, juntamente com o nome de arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="c1c75-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1c75-104">Esse método pode ser chamado apenas uma vez e deve ser chamado antes de quaisquer outros métodos de leitor.</span><span class="sxs-lookup"><span data-stu-id="c1c75-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1c75-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1c75-105">Syntax</span></span>  
  
```  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1c75-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c1c75-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="c1c75-107">[in] A interface de Importador de metadados com o qual esse leitor será associado.</span><span class="sxs-lookup"><span data-stu-id="c1c75-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="c1c75-108">[in] O nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="c1c75-108">[in] The file name of the module.</span></span> <span data-ttu-id="c1c75-109">Você pode usar o `pIStream` parâmetro em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c1c75-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="c1c75-110">[in] O caminho para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="c1c75-110">[in] The path to search.</span></span> <span data-ttu-id="c1c75-111">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="c1c75-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="c1c75-112">[in] O fluxo de arquivos, usado como uma alternativa para o parâmetro de nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c1c75-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1c75-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c1c75-113">Return Value</span></span>  
 <span data-ttu-id="c1c75-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c1c75-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1c75-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1c75-115">Remarks</span></span>  
 <span data-ttu-id="c1c75-116">Você precisa especificar apenas um dos `filename` ou o `pIStream` parâmetros, não ambos.</span><span class="sxs-lookup"><span data-stu-id="c1c75-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="c1c75-117">O parâmetro `searchPath` é opcional.</span><span class="sxs-lookup"><span data-stu-id="c1c75-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1c75-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c1c75-118">Requirements</span></span>  
 <span data-ttu-id="c1c75-119">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1c75-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1c75-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1c75-120">See also</span></span>

- [<span data-ttu-id="c1c75-121">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="c1c75-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
