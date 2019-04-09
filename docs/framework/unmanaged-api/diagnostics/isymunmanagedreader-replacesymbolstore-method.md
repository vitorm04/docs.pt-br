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
ms.openlocfilehash: 34d93c6956ff391e4d8726d8e45265c96947ad4c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154759"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="84180-102">Método ISymUnmanagedReader::ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="84180-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="84180-103">Substitui o repositório de símbolos existente por um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="84180-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="84180-104">Esse método é semelhante para o [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) método, exceto pelo fato do delta de determinado atua como uma substituição completa em vez de uma atualização.</span><span class="sxs-lookup"><span data-stu-id="84180-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84180-105">Você precisa especificar apenas um dos `filename` ou `pIStream` parâmetros, não ambos.</span><span class="sxs-lookup"><span data-stu-id="84180-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="84180-106">Se `filename` for especificado, o repositório de símbolos será atualizado com os símbolos no arquivo.</span><span class="sxs-lookup"><span data-stu-id="84180-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="84180-107">Se `pIStream` for especificado, o repositório será atualizado com os dados a partir de <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="84180-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84180-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="84180-108">Syntax</span></span>  
  
```  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84180-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="84180-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="84180-110">[in] O nome do arquivo que contém o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="84180-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="84180-111">[in] O fluxo de arquivos, usado como uma alternativa para o `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="84180-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84180-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="84180-112">Return Value</span></span>  
 <span data-ttu-id="84180-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="84180-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84180-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="84180-114">Requirements</span></span>  
 <span data-ttu-id="84180-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="84180-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84180-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="84180-116">See also</span></span>

- [<span data-ttu-id="84180-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="84180-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
