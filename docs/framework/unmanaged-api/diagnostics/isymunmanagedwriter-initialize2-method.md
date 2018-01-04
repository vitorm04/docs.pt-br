---
title: "Método ISymUnmanagedWriter::Initialize2"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.Initialize2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 015c7d43a856990251b3e67febe685759cc4e5fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="1e202-102">Método ISymUnmanagedWriter::Initialize2</span><span class="sxs-lookup"><span data-stu-id="1e202-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="1e202-103">Define a interface do emissor de metadados com a qual este gravador será associado e define o nome do arquivo de saída que serão gravados os símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="1e202-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="1e202-104">Esse método também permite definir o local final do arquivo de banco de dados (PDB) do programa.</span><span class="sxs-lookup"><span data-stu-id="1e202-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e202-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e202-105">Syntax</span></span>  
  
```  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e202-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1e202-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="1e202-107">[in] Um ponteiro para a interface do emissor de metadados.</span><span class="sxs-lookup"><span data-stu-id="1e202-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="1e202-108">[in] Um ponteiro para um `WCHAR` que contém o nome do arquivo no qual os símbolos de depuração são gravados.</span><span class="sxs-lookup"><span data-stu-id="1e202-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="1e202-109">Se um nome de arquivo for especificado para um gravador que não use nomes de arquivo, esse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="1e202-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="1e202-110">[in] Se especificado, o gravador de símbolo emite os símbolos para o determinado <xref:System.Runtime.InteropServices.ComTypes.IStream> em vez de no arquivo especificado no `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="1e202-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="1e202-111">O parâmetro `pIStream` é opcional.</span><span class="sxs-lookup"><span data-stu-id="1e202-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="1e202-112">[in] `true` quando se trata de uma recriação completa; `false` quando se trata de uma compilação incremental.</span><span class="sxs-lookup"><span data-stu-id="1e202-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="1e202-113">[in] Um ponteiro para um `WCHAR` que é a cadeia de caracteres de caminho para o local final do arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="1e202-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1e202-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1e202-114">Return Value</span></span>  
 <span data-ttu-id="1e202-115">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1e202-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e202-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1e202-116">Requirements</span></span>  
 <span data-ttu-id="1e202-117">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1e202-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e202-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e202-118">See Also</span></span>  
 [<span data-ttu-id="1e202-119">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="1e202-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="1e202-120">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="1e202-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
