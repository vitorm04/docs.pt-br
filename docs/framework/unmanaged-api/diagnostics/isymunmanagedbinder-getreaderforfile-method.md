---
title: Método ISymUnmanagedBinder::GetReaderForFile
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderForFile
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderForFile
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderForFile method [.NET Framework debugging]
- GetReaderForFile method [.NET Framework debugging]
ms.assetid: 46c06258-831e-47c8-a50a-8650af6b637e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0414cadca910f3290f96a841e3f807f0de469606
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145958"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="21204-102">Método ISymUnmanagedBinder::GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="21204-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="21204-103">Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface que lê os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="21204-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="21204-104">Esse método abrirá o arquivo de programa (PDB) do banco de dados somente se ele está ao lado do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="21204-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="21204-105">Essa alteração foi feita para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="21204-105">This change has been made for security purposes.</span></span> <span data-ttu-id="21204-106">Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="21204-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21204-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="21204-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21204-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="21204-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="21204-109">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="21204-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="21204-110">[in] Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="21204-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="21204-111">[in] Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="21204-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="21204-112">[out] Um ponteiro que é definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="21204-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21204-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="21204-113">Return Value</span></span>  
 <span data-ttu-id="21204-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="21204-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21204-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="21204-115">Requirements</span></span>  
 <span data-ttu-id="21204-116">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="21204-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21204-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="21204-117">See also</span></span>

- [<span data-ttu-id="21204-118">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="21204-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="21204-119">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="21204-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
