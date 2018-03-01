---
title: "Método ISymUnmanagedReader::UpdateSymbolStore"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 267037cbdf9e9bf45454bd8b584563ba1ecd847d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreaderupdatesymbolstore-method"></a><span data-ttu-id="40fc7-102">Método ISymUnmanagedReader::UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="40fc7-102">ISymUnmanagedReader::UpdateSymbolStore Method</span></span>
<span data-ttu-id="40fc7-103">Atualiza o armazenamento de símbolo existente com um armazenamento de símbolo de delta.</span><span class="sxs-lookup"><span data-stu-id="40fc7-103">Updates the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="40fc7-104">Esse método é usado em cenários de editar e continuar para atualizar o repositório de símbolos para corresponder deltas para o arquivo executável (PE) portátil original.</span><span class="sxs-lookup"><span data-stu-id="40fc7-104">This method is used in edit-and-continue scenarios to update the symbol store to match deltas to the original portable executable (PE) file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40fc7-105">É necessário especificar apenas uma da `filename` ou `pIStream` parâmetros, não ambos.</span><span class="sxs-lookup"><span data-stu-id="40fc7-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="40fc7-106">Se `filename` for especificado, o armazenamento de símbolo será atualizado com os símbolos no arquivo.</span><span class="sxs-lookup"><span data-stu-id="40fc7-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="40fc7-107">Se `pIStream` for especificado, o repositório será atualizado com os dados a partir de <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span><span class="sxs-lookup"><span data-stu-id="40fc7-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40fc7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="40fc7-108">Syntax</span></span>  
  
```  
HRESULT UpdateSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="40fc7-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="40fc7-109">Parameters</span></span>  
 `filename`  
 <span data-ttu-id="40fc7-110">[in] O nome do arquivo que contém o armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="40fc7-110">[in] The name of the file that contains the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="40fc7-111">[in] O fluxo de arquivos, usado como uma alternativa para o `filename` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="40fc7-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40fc7-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="40fc7-112">Return Value</span></span>  
 <span data-ttu-id="40fc7-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="40fc7-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40fc7-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="40fc7-114">Requirements</span></span>  
 <span data-ttu-id="40fc7-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="40fc7-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40fc7-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40fc7-116">See Also</span></span>  
 [<span data-ttu-id="40fc7-117">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="40fc7-117">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
