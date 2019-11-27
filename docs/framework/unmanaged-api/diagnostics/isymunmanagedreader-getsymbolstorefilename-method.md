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
ms.openlocfilehash: b3674c4058dba2f6185418b55b35eefb14c312f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431232"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="678c8-102">Método ISymUnmanagedReader::GetSymbolStoreFileName</span><span class="sxs-lookup"><span data-stu-id="678c8-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>
<span data-ttu-id="678c8-103">Fornece o nome de arquivo em disco do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="678c8-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="678c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="678c8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="678c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="678c8-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="678c8-106">no O tamanho do buffer de `szName`.</span><span class="sxs-lookup"><span data-stu-id="678c8-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="678c8-107">fora Um ponteiro para a variável que recebe o comprimento do nome retornado em `szName`, incluindo a terminação nula.</span><span class="sxs-lookup"><span data-stu-id="678c8-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="678c8-108">fora Um ponteiro para a variável que recebe o nome de arquivo do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="678c8-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="678c8-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="678c8-109">Return Value</span></span>  
 <span data-ttu-id="678c8-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="678c8-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="678c8-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="678c8-111">Requirements</span></span>  
 <span data-ttu-id="678c8-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="678c8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="678c8-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="678c8-113">See also</span></span>

- [<span data-ttu-id="678c8-114">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="678c8-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
