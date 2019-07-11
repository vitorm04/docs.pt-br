---
title: Método ISymUnmanagedReader::GetSymbolStoreFileName
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 50cd6d1e3666dd1f15c1e6a6b4f7dcb931b79d8d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777071"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="f15a2-102">Método ISymUnmanagedReader::GetSymbolStoreFileName</span><span class="sxs-lookup"><span data-stu-id="f15a2-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="f15a2-103">Fornece o nome de arquivo em disco do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f15a2-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f15a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f15a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f15a2-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="f15a2-106">[in] O tamanho do `szName` buffer.</span><span class="sxs-lookup"><span data-stu-id="f15a2-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="f15a2-107">[out] Um ponteiro para a variável que recebe o comprimento do nome retornado no `szName`, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="f15a2-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="f15a2-108">[out] Um ponteiro para a variável que recebe o nome do arquivo de repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f15a2-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f15a2-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f15a2-109">Return Value</span></span>  
 <span data-ttu-id="f15a2-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f15a2-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15a2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f15a2-111">Requirements</span></span>  
 <span data-ttu-id="f15a2-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f15a2-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15a2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f15a2-113">See also</span></span>

- [<span data-ttu-id="f15a2-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f15a2-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
