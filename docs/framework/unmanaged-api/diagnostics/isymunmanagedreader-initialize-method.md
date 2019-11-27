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
ms.openlocfilehash: ca34d1d84d6f9960d021c35566f8412df321464d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429742"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="97b72-102">Método ISymUnmanagedReader::Initialize</span><span class="sxs-lookup"><span data-stu-id="97b72-102">ISymUnmanagedReader::Initialize Method</span></span>
<span data-ttu-id="97b72-103">Inicializa o leitor de símbolos com a interface de importador de metadados à qual esse leitor será associado, juntamente com o nome de arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="97b72-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="97b72-104">Esse método pode ser chamado apenas uma vez e deve ser chamado antes de qualquer outro método de leitura.</span><span class="sxs-lookup"><span data-stu-id="97b72-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97b72-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97b72-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97b72-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97b72-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="97b72-107">no A interface de importador de metadados à qual este leitor será associado.</span><span class="sxs-lookup"><span data-stu-id="97b72-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="97b72-108">no O nome do arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="97b72-108">[in] The file name of the module.</span></span> <span data-ttu-id="97b72-109">Em vez disso, você pode usar o parâmetro `pIStream`.</span><span class="sxs-lookup"><span data-stu-id="97b72-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="97b72-110">no O caminho para pesquisar.</span><span class="sxs-lookup"><span data-stu-id="97b72-110">[in] The path to search.</span></span> <span data-ttu-id="97b72-111">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="97b72-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="97b72-112">no O fluxo de arquivos, usado como uma alternativa ao parâmetro filename.</span><span class="sxs-lookup"><span data-stu-id="97b72-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97b72-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="97b72-113">Return Value</span></span>  
 <span data-ttu-id="97b72-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="97b72-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97b72-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="97b72-115">Remarks</span></span>  
 <span data-ttu-id="97b72-116">Você precisa especificar apenas um dos parâmetros `filename` ou `pIStream`, não ambos.</span><span class="sxs-lookup"><span data-stu-id="97b72-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="97b72-117">O parâmetro `searchPath` é opcional.</span><span class="sxs-lookup"><span data-stu-id="97b72-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97b72-118">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="97b72-118">Requirements</span></span>  
 <span data-ttu-id="97b72-119">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="97b72-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97b72-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97b72-120">See also</span></span>

- [<span data-ttu-id="97b72-121">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="97b72-121">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
