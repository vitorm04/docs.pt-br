---
title: Método ISymUnmanagedBinder2::GetReaderForFile2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2.GetReaderForFile2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2
helpviewer_keywords:
- ISymUnmanagedBinder2::GetReaderForFile2 method [.NET Framework debugging]
- GetReaderForFile2 method [.NET Framework debugging]
ms.assetid: dd92dcaf-403c-464d-a254-21594985dddd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e133333d735ca53d194bbb535710bc62bde6bb0e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188450"
---
# <a name="isymunmanagedbinder2getreaderforfile2-method"></a><span data-ttu-id="1cdb3-102">Método ISymUnmanagedBinder2::GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="1cdb3-102">ISymUnmanagedBinder2::GetReaderForFile2 Method</span></span>
<span data-ttu-id="1cdb3-103">Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface que lê os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-103">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span>  
  
 <span data-ttu-id="1cdb3-104">Esse método fornece uma pesquisa mais abrangente para o arquivo de banco de dados (PDB) do programa que o [isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-104">This method provides a more extensive search for the program database (PDB) file than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cdb3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cdb3-105">Syntax</span></span>  
  
```  
HRESULT GetReaderForFile2(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cdb3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1cdb3-106">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="1cdb3-107">[in] Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="1cdb3-108">[in] Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-108">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="1cdb3-109">[in] Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-109">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="1cdb3-110">[in] Um valor igual a [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeração que especifica a política a ser usada ao fazer uma pesquisa por um leitor de símbolo.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-110">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="1cdb3-111">[out] Um ponteiro que é definido para retornado [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cdb3-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1cdb3-112">Return Value</span></span>  
 <span data-ttu-id="1cdb3-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cdb3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cdb3-114">Requirements</span></span>  
 <span data-ttu-id="1cdb3-115">**Cabeçalho:** Corsym, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1cdb3-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cdb3-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cdb3-116">Remarks</span></span>  
 <span data-ttu-id="1cdb3-117">Esta versão do método pode procurar o arquivo PDB em áreas que não seja bem ao lado do módulo.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-117">This version of the method can search for the PDB file in areas other than right next to the module.</span></span> <span data-ttu-id="1cdb3-118">A política de pesquisa pode ser controlada pela combinação [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="1cdb3-118">The search policy can be controlled by combining [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md).</span></span> <span data-ttu-id="1cdb3-119">Por exemplo, `AllowReferencePathAccess | AllowSymbolServerAccess` procura o PDB ao lado do arquivo executável e, em um servidor de símbolo, mas não consultar o registro ou use o caminho do arquivo executável.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-119">For example, `AllowReferencePathAccess | AllowSymbolServerAccess` looks for the PDB next to the executable file and on a symbol server, but does not query the registry or use the path in the executable file.</span></span> <span data-ttu-id="1cdb3-120">Se o `searchPath` parâmetro for fornecido, esses diretórios sempre serão pesquisados.</span><span class="sxs-lookup"><span data-stu-id="1cdb3-120">If the `searchPath` parameter is provided, those directories will always be searched.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cdb3-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1cdb3-121">See Also</span></span>  
 [<span data-ttu-id="1cdb3-122">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="1cdb3-122">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="1cdb3-123">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="1cdb3-123">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)
