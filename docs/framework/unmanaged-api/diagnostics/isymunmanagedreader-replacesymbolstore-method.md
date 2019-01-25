---
title: Método ISymUnmanagedReader::ReplaceSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f06c416d3443b350a172fab1a93a5d72bf40c197
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740353"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="93071-102">Método ISymUnmanagedReader::ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="93071-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="93071-103">Substitui o repositório de símbolos existente por um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="93071-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="93071-104">Esse método é semelhante para o [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) método, exceto pelo fato do delta de determinado atua como uma substituição completa em vez de uma atualização.</span><span class="sxs-lookup"><span data-stu-id="93071-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="93071-105">Você precisa especificar apenas um dos `filename` ou `pIStream` parâmetros, não ambos.</span><span class="sxs-lookup"><span data-stu-id="93071-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="93071-106">Se `filename` for especificado, o repositório de símbolos será atualizado com os símbolos no arquivo.</span><span class="sxs-lookup"><span data-stu-id="93071-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="93071-107">Se `pIStream` for especificado, o repositório será atualizado com os dados a partir de <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="93071-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93071-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="93071-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="93071-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="93071-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="93071-110">[in] O nome do arquivo que contém o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="93071-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="93071-111">[in] O fluxo de arquivos, usado como uma alternativa para o `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="93071-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93071-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="93071-112">Return Value</span></span>  
 <span data-ttu-id="93071-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="93071-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93071-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="93071-114">Requirements</span></span>  
 <span data-ttu-id="93071-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="93071-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93071-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93071-116">See also</span></span>
- [<span data-ttu-id="93071-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="93071-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
