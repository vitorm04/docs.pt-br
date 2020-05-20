---
title: Método ISymUnmanagedBinder3::GetReaderFromCallback
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
ms.openlocfilehash: 4a23e9aa259f430c0d0579657952fc6aba4c307c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441650"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="d72a3-102">Método ISymUnmanagedBinder3::GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="d72a3-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="d72a3-103">Permite que o usuário implemente ou forneça por meio de um retorno de chamada `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações do diretório de depuração da memória.</span><span class="sxs-lookup"><span data-stu-id="d72a3-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d72a3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d72a3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d72a3-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d72a3-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="d72a3-106">no Um ponteiro para a interface de importação de metadados.</span><span class="sxs-lookup"><span data-stu-id="d72a3-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="d72a3-107">no Um ponteiro para o nome do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d72a3-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="d72a3-108">no Um ponteiro para o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="d72a3-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="d72a3-109">no Um valor da enumeração [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) que especifica a política a ser usada ao fazer uma pesquisa por um leitor de símbolo.</span><span class="sxs-lookup"><span data-stu-id="d72a3-109">[in] A value of the [CorSymSearchPolicyAttributes](corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="d72a3-110">no Um ponteiro para a função de retorno de chamada.</span><span class="sxs-lookup"><span data-stu-id="d72a3-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="d72a3-111">fora Um ponteiro que é definido para a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) retornada.</span><span class="sxs-lookup"><span data-stu-id="d72a3-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d72a3-112">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="d72a3-112">Return Value</span></span>  
 <span data-ttu-id="d72a3-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d72a3-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d72a3-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d72a3-114">Requirements</span></span>  
 <span data-ttu-id="d72a3-115">**Cabeçalho:** CorSym. idl</span><span class="sxs-lookup"><span data-stu-id="d72a3-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d72a3-116">Confira também</span><span class="sxs-lookup"><span data-stu-id="d72a3-116">See also</span></span>

- [<span data-ttu-id="d72a3-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="d72a3-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
