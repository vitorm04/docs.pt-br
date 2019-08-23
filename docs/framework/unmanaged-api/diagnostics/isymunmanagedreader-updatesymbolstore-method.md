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
ms.openlocfilehash: d84d4fccb2cb4e500f07f6bfbfb93b8c7b81f5d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939000"
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="e9029-102">Método ISymUnmanagedReader::UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="e9029-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="e9029-103">Atualiza o repositório de símbolos existente com um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="e9029-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="e9029-104">Esse método é usado em cenários de edição e continuação para atualizar o armazenamento de símbolo para corresponder deltas ao arquivo PE (executável portátil) original.</span><span class="sxs-lookup"><span data-stu-id="e9029-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9029-105">Você precisa especificar apenas um dos `filename` parâmetros ou `pIStream` , não ambos.</span><span class="sxs-lookup"><span data-stu-id="e9029-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="e9029-106">Se `filename` for especificado, o armazenamento de símbolos será atualizado com os símbolos nesse arquivo.</span><span class="sxs-lookup"><span data-stu-id="e9029-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="e9029-107">Se `pIStream` for especificado, o repositório será atualizado com os dados <xref:System.Runtime.InteropServices.ComTypes.IStream>do.</span><span class="sxs-lookup"><span data-stu-id="e9029-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9029-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9029-108">Syntax</span></span>  
  
```cpp  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9029-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e9029-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="e9029-110">no O nome do arquivo que contém o armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="e9029-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="e9029-111">no O fluxo de arquivos, usado como uma alternativa ao `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="e9029-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9029-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e9029-112">Return Value</span></span>  
 <span data-ttu-id="e9029-113">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e9029-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9029-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9029-114">Requirements</span></span>  
 <span data-ttu-id="e9029-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e9029-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9029-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9029-116">See also</span></span>

- [<span data-ttu-id="e9029-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="e9029-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
