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
ms.openlocfilehash: 8721f7c30061fbfd4a761bed090b761762c3c13c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939033"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="75b27-102">Método ISymUnmanagedReader::ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="75b27-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>
<span data-ttu-id="75b27-103">Substitui o repositório de símbolos existente por um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="75b27-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="75b27-104">Esse método é semelhante ao método [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) , exceto que o Delta fornecido atua como uma substituição completa em vez de uma atualização.</span><span class="sxs-lookup"><span data-stu-id="75b27-104">This method is similar to the [UpdateSymbolStore](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75b27-105">Você precisa especificar apenas um dos `filename` parâmetros ou `pIStream` , não ambos.</span><span class="sxs-lookup"><span data-stu-id="75b27-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="75b27-106">Se `filename` for especificado, o armazenamento de símbolos será atualizado com os símbolos nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="75b27-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="75b27-107">Se `pIStream` for especificado, o repositório será atualizado com os dados <xref:System.Runtime.InteropServices.ComTypes.IStream>do.</span><span class="sxs-lookup"><span data-stu-id="75b27-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75b27-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75b27-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="75b27-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="75b27-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="75b27-110">no O nome do arquivo que contém o armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="75b27-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="75b27-111">no O fluxo de arquivos, usado como uma alternativa ao `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="75b27-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="75b27-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="75b27-112">Return Value</span></span>  
 <span data-ttu-id="75b27-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="75b27-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75b27-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="75b27-114">Requirements</span></span>  
 <span data-ttu-id="75b27-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="75b27-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75b27-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75b27-116">See also</span></span>

- [<span data-ttu-id="75b27-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="75b27-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
