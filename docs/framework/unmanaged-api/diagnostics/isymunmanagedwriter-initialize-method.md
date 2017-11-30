---
title: "Método ISymUnmanagedWriter::Initialize"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: e0ebd793-3764-4df0-8f12-0e95f60b9eae
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bae368919941e6a0b234736f789320b62405a17b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedwriterinitialize-method"></a><span data-ttu-id="c69b4-102">Método ISymUnmanagedWriter::Initialize</span><span class="sxs-lookup"><span data-stu-id="c69b4-102">ISymUnmanagedWriter::Initialize Method</span></span>
<span data-ttu-id="c69b4-103">Define a interface do emissor de metadados com a qual este gravador será associado e define o nome do arquivo de saída que serão gravados os símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="c69b4-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>  
  
 <span data-ttu-id="c69b4-104">Esse método pode ser chamado apenas uma vez, e ele deve ser chamado antes de quaisquer outros métodos de gravador.</span><span class="sxs-lookup"><span data-stu-id="c69b4-104">This method can be called only once, and it must be called before any other writer methods.</span></span> <span data-ttu-id="c69b4-105">Alguns gravadores podem exigir um nome de arquivo.</span><span class="sxs-lookup"><span data-stu-id="c69b4-105">Some writers may require a file name.</span></span> <span data-ttu-id="c69b4-106">No entanto, você sempre pode passar um nome de arquivo para esse método sem qualquer efeito negativo no gravadores que não usam o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="c69b4-106">However, you can always pass a file name to this method without any negative effect on writers that do not use the file name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c69b4-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c69b4-107">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *filename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c69b4-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c69b4-108">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="c69b4-109">[in] Um ponteiro para a interface do emissor de metadados.</span><span class="sxs-lookup"><span data-stu-id="c69b4-109">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `filename`  
 <span data-ttu-id="c69b4-110">[in] O nome do arquivo no qual os símbolos de depuração são gravados.</span><span class="sxs-lookup"><span data-stu-id="c69b4-110">[in] The file name to which the debugging symbols are written.</span></span> <span data-ttu-id="c69b4-111">Se um nome de arquivo for especificado para um gravador que não use nomes de arquivo, esse parâmetro é ignorado.</span><span class="sxs-lookup"><span data-stu-id="c69b4-111">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="c69b4-112">[in] Se especificado, o gravador de símbolo emitirá os símbolos para o determinado <xref:System.Runtime.InteropServices.ComTypes.IStream> em vez de no arquivo especificado no `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c69b4-112">[in] If specified, the symbol writer will emit the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="c69b4-113">O parâmetro `pIStream` é opcional.</span><span class="sxs-lookup"><span data-stu-id="c69b4-113">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="c69b4-114">[in] `true` quando se trata de uma recriação completa; `false` quando se trata de uma compilação incremental.</span><span class="sxs-lookup"><span data-stu-id="c69b4-114">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c69b4-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c69b4-115">Return Value</span></span>  
 <span data-ttu-id="c69b4-116">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c69b4-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c69b4-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c69b4-117">Requirements</span></span>  
 <span data-ttu-id="c69b4-118">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c69b4-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c69b4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c69b4-119">See Also</span></span>  
 [<span data-ttu-id="c69b4-120">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="c69b4-120">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="c69b4-121">Método Initialize2</span><span class="sxs-lookup"><span data-stu-id="c69b4-121">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)
