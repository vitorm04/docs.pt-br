---
title: "Método ISymUnmanagedWriter::GetDebugInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="d66b7-102">Método ISymUnmanagedWriter::GetDebugInfo</span><span class="sxs-lookup"><span data-stu-id="d66b7-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="d66b7-103">Retorna as informações necessárias para que um compilador gravar a entrada de diretório de depuração no cabeçalho de arquivo executável (PE) do portátil.</span><span class="sxs-lookup"><span data-stu-id="d66b7-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="d66b7-104">O gravador de símbolo preenche todos os campos, exceto para `TimeDateStamp` e `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="d66b7-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="d66b7-105">(O compilador é responsável por definir esses dois campos adequadamente.)</span><span class="sxs-lookup"><span data-stu-id="d66b7-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="d66b7-106">Um compilador deve chamar esse método, emitir o blob de dados para o arquivo PE, defina o `PointerToRawData` campo IMAGE_DEBUG_DIRECTORY para apontar para os dados emitidos e gravar o IMAGE_DEBUG_DIRECTORY arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="d66b7-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="d66b7-107">O compilador também deve definir o `TimeDateStamp` campos para igualar o `TimeDateStamp` do arquivo PE que está sendo gerado.</span><span class="sxs-lookup"><span data-stu-id="d66b7-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d66b7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d66b7-108">Syntax</span></span>  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d66b7-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d66b7-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="d66b7-110">[out no] Um ponteiro para um IMAGE_DEBUG_DIRECTORY que preencherá o gravador de símbolo.</span><span class="sxs-lookup"><span data-stu-id="d66b7-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="d66b7-111">[in] Um `DWORD` que contém o tamanho dos dados de depuração.</span><span class="sxs-lookup"><span data-stu-id="d66b7-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="d66b7-112">[out] Um ponteiro para um `DWORD` que recebe o tamanho do buffer necessário para conter os dados de depuração.</span><span class="sxs-lookup"><span data-stu-id="d66b7-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="d66b7-113">[out] Um ponteiro para um buffer que é grande o suficiente para manter os dados de depuração para o armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="d66b7-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d66b7-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="d66b7-114">Return Value</span></span>  
 <span data-ttu-id="d66b7-115">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="d66b7-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d66b7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d66b7-116">Requirements</span></span>  
 <span data-ttu-id="d66b7-117">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d66b7-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d66b7-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d66b7-118">See Also</span></span>  
 [<span data-ttu-id="d66b7-119">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="d66b7-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
