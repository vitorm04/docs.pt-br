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
ms.openlocfilehash: df6a35dcaebc681aa5463a014d3283c81efea617
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199858"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="69b49-102">Método ISymUnmanagedBinder::GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="69b49-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="69b49-103">Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface que lê os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="69b49-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="69b49-104">Esse método abrirá o arquivo de programa (PDB) do banco de dados somente se ele está ao lado do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="69b49-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="69b49-105">Essa alteração foi feita para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="69b49-105">This change has been made for security purposes.</span></span> <span data-ttu-id="69b49-106">Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="69b49-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b49-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69b49-107">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b49-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="69b49-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="69b49-109">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="69b49-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="69b49-110">[in] Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="69b49-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="69b49-111">[in] Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="69b49-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="69b49-112">[out] Um ponteiro que é definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="69b49-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69b49-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="69b49-113">Return Value</span></span>  
 <span data-ttu-id="69b49-114">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="69b49-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b49-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="69b49-115">Requirements</span></span>  
 <span data-ttu-id="69b49-116">**Cabeçalho:** Corsym, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="69b49-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b49-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69b49-117">See Also</span></span>  
 [<span data-ttu-id="69b49-118">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="69b49-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="69b49-119">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="69b49-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
