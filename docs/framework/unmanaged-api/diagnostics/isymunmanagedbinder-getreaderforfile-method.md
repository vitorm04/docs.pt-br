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
ms.openlocfilehash: 94cda16466ea5a3d35a478a2ae80281e9414f719
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449365"
---
# <a name="isymunmanagedbindergetreaderforfile-method"></a><span data-ttu-id="818de-102">Método ISymUnmanagedBinder::GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="818de-102">ISymUnmanagedBinder::GetReaderForFile Method</span></span>
<span data-ttu-id="818de-103">Dada uma interface de metadados e um nome de arquivo, retorna a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="818de-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="818de-104">Esse método abrirá o arquivo de banco de dados do programa (PDB) somente se ele estiver próximo ao arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="818de-104">This method will open the program database (PDB) file only if it is next to the executable file.</span></span> <span data-ttu-id="818de-105">Essa alteração foi feita para fins de segurança.</span><span class="sxs-lookup"><span data-stu-id="818de-105">This change has been made for security purposes.</span></span> <span data-ttu-id="818de-106">Se você precisar de uma pesquisa mais abrangente para o arquivo PDB, use o método [ISymUnmanagedBinder2:: GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="818de-106">If you need a more extensive search for the PDB file, use the [ISymUnmanagedBinder2::GetReaderForFile2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="818de-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="818de-107">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderForFile(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [out, retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="818de-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="818de-108">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="818de-109">no Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="818de-109">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="818de-110">no Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="818de-110">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="818de-111">no Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="818de-111">[in] A pointer to the search path.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="818de-112">fora Um ponteiro que é definido para a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="818de-112">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="818de-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="818de-113">Return Value</span></span>  
 <span data-ttu-id="818de-114">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="818de-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="818de-115">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="818de-115">Requirements</span></span>  
 <span data-ttu-id="818de-116">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="818de-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="818de-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="818de-117">See also</span></span>

- [<span data-ttu-id="818de-118">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="818de-118">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="818de-119">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="818de-119">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)
