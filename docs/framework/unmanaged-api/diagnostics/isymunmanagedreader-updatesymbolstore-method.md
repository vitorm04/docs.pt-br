---
title: Método ISymUnmanagedReader::UpdateSymbolStore
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.UpdateSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::UpdateSymbolStore
helpviewer_keywords:
- UpdateSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::UpdateSymbolStore method [.NET Framework debugging]
ms.assetid: 4a17d723-86b9-4f27-bd0d-b70c3259011c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52a1f30612899fddc29af1a437fb9437e9a2b93c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490691"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="108aa-102">Método ISymUnmanagedReader::UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="108aa-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="108aa-103">Atualiza o repositório de símbolos existente com um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="108aa-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="108aa-104">Esse método é usado em cenários de editar e continuar para atualizar o repositório de símbolos para corresponder os deltas para o original (arquivo portable Executable).</span><span class="sxs-lookup"><span data-stu-id="108aa-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="108aa-105">Você precisa especificar apenas um dos `filename` ou `pIStream` parâmetros, não ambos.</span><span class="sxs-lookup"><span data-stu-id="108aa-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="108aa-106">Se `filename` for especificado, o repositório de símbolos será atualizado com os símbolos no arquivo.</span><span class="sxs-lookup"><span data-stu-id="108aa-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="108aa-107">Se `pIStream` for especificado, o repositório será atualizado com os dados a partir de <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="108aa-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="108aa-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="108aa-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="108aa-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="108aa-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="108aa-110">[in] O nome do arquivo que contém o repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="108aa-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="108aa-111">[in] O fluxo de arquivos, usado como uma alternativa para o `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="108aa-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="108aa-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="108aa-112">Return Value</span></span>  
 <span data-ttu-id="108aa-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="108aa-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="108aa-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="108aa-114">Requirements</span></span>  
 <span data-ttu-id="108aa-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="108aa-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="108aa-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="108aa-116">See also</span></span>
- [<span data-ttu-id="108aa-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="108aa-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
