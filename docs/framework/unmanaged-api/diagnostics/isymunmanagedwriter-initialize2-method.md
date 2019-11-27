---
title: Método ISymUnmanagedWriter::Initialize2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Initialize2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Initialize2
helpviewer_keywords:
- ISymUnmanagedWriter::Initialize2 method [.NET Framework debugging]
- Initialize2 method [.NET Framework debugging]
ms.assetid: 93de56b6-4ae8-4cca-acdc-25a434623509
topic_type:
- apiref
ms.openlocfilehash: 041df959139a0be77f40d6aa5655ff15f93fb26f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427947"
---
# <a name="isymunmanagedwriterinitialize2-method"></a><span data-ttu-id="67f62-102">Método ISymUnmanagedWriter::Initialize2</span><span class="sxs-lookup"><span data-stu-id="67f62-102">ISymUnmanagedWriter::Initialize2 Method</span></span>
<span data-ttu-id="67f62-103">Define a interface do emissor de metadados com a qual esse gravador será associado e define o nome do arquivo de saída para o qual os símbolos de depuração serão gravados.</span><span class="sxs-lookup"><span data-stu-id="67f62-103">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span> <span data-ttu-id="67f62-104">Esse método também permite que você defina o local final do arquivo de banco de dados do programa (PDB).</span><span class="sxs-lookup"><span data-stu-id="67f62-104">This method also lets you set the final location of the program database (PDB) file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67f62-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67f62-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize2(  
    [in] IUnknown     *emitter,  
    [in] const WCHAR  *tempfilename,  
    [in] IStream      *pIStream,  
    [in] BOOL         fFullBuild,  
    [in] const WCHAR  *finalfilename);  
```  
  
## <a name="parameters"></a><span data-ttu-id="67f62-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67f62-106">Parameters</span></span>  
 `emitter`  
 <span data-ttu-id="67f62-107">no Um ponteiro para a interface do emissor de metadados.</span><span class="sxs-lookup"><span data-stu-id="67f62-107">[in] A pointer to the metadata emitter interface.</span></span>  
  
 `tempfilename`  
 <span data-ttu-id="67f62-108">no Um ponteiro para um `WCHAR` que contém o nome do arquivo para o qual os símbolos de depuração são gravados.</span><span class="sxs-lookup"><span data-stu-id="67f62-108">[in] A pointer to a `WCHAR` that contains the file name to which the debugging symbols are written.</span></span> <span data-ttu-id="67f62-109">Se um nome de arquivo for especificado para um gravador que não use nomes de arquivo, esse parâmetro será ignorado.</span><span class="sxs-lookup"><span data-stu-id="67f62-109">If a file name is specified for a writer that does not use file names, this parameter is ignored.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="67f62-110">no Se especificado, o gravador de símbolo emitirá os símbolos para o determinado <xref:System.Runtime.InteropServices.ComTypes.IStream> em vez de para o arquivo especificado no parâmetro `filename`.</span><span class="sxs-lookup"><span data-stu-id="67f62-110">[in] If specified, the symbol writer emits the symbols into the given <xref:System.Runtime.InteropServices.ComTypes.IStream> rather than to the file specified in the `filename` parameter.</span></span> <span data-ttu-id="67f62-111">O parâmetro `pIStream` é opcional.</span><span class="sxs-lookup"><span data-stu-id="67f62-111">The `pIStream` parameter is optional.</span></span>  
  
 `fFullBuild`  
 <span data-ttu-id="67f62-112">[in] `true` se esta for uma recompilação completa; `false` se esta for uma compilação incremental.</span><span class="sxs-lookup"><span data-stu-id="67f62-112">[in] `true` if this is a full rebuild; `false` if this is an incremental compilation.</span></span>  
  
 `finalfilename`  
 <span data-ttu-id="67f62-113">no Um ponteiro para um `WCHAR` que é a cadeia de caracteres de caminho para o local final do arquivo PDB.</span><span class="sxs-lookup"><span data-stu-id="67f62-113">[in] A pointer to a `WCHAR` that is the path string to the final location of the PDB file.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="67f62-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="67f62-114">Return Value</span></span>  
 <span data-ttu-id="67f62-115">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="67f62-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67f62-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="67f62-116">Requirements</span></span>  
 <span data-ttu-id="67f62-117">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="67f62-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67f62-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67f62-118">See also</span></span>

- [<span data-ttu-id="67f62-119">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="67f62-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="67f62-120">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="67f62-120">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)
