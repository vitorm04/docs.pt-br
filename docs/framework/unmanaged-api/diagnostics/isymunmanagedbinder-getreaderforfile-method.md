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
ms.openlocfilehash: c4416e8e4395c4e1967155310d12a1eb68c42d83
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441728"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="2e3af-102">Método ISymUnmanagedBinder::GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="2e3af-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="2e3af-103">Dada uma interface de metadados e um nome de arquivo, retorna a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="2e3af-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="2e3af-104">Esse método abrirá o arquivo de banco de dados do programa (PDB) somente se ele estiver próximo ao arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="2e3af-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="2e3af-105">Essa alteração foi feita para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="2e3af-105">This change has been made for security purposes.</span></span> <span data-ttu-id="2e3af-106">Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o método [ISymUnmanagedBinder2:: GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2e3af-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e3af-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2e3af-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e3af-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2e3af-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="2e3af-109">no Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="2e3af-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="2e3af-110">no Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="2e3af-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="2e3af-111">no Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="2e3af-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="2e3af-112">fora Um ponteiro que é definido para a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="2e3af-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e3af-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2e3af-113">Return Value</span></span>  
 <span data-ttu-id="2e3af-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2e3af-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3af-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2e3af-115">Requirements</span></span>  
 <span data-ttu-id="2e3af-116">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2e3af-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e3af-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="2e3af-117">See also</span></span>

- [<span data-ttu-id="2e3af-118">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="2e3af-118">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="2e3af-119">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="2e3af-119">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)
