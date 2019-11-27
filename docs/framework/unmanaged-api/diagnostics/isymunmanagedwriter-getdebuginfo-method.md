---
title: Método ISymUnmanagedWriter::GetDebugInfo
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.GetDebugInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type:
- apiref
ms.openlocfilehash: 2b901a3dac499f1ce3f843c59122dd8fd5022147
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427956"
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a><span data-ttu-id="8ffa2-102">Método ISymUnmanagedWriter::GetDebugInfo</span><span class="sxs-lookup"><span data-stu-id="8ffa2-102">ISymUnmanagedWriter::GetDebugInfo Method</span></span>
<span data-ttu-id="8ffa2-103">Retorna as informações necessárias para um compilador gravar a entrada do diretório de depuração no cabeçalho do arquivo PE (executável portátil).</span><span class="sxs-lookup"><span data-stu-id="8ffa2-103">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span> <span data-ttu-id="8ffa2-104">O gravador de símbolos preenche todos os campos, exceto `TimeDateStamp` e `PointerToRawData`.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-104">The symbol writer fills out all fields except for `TimeDateStamp` and `PointerToRawData`.</span></span> <span data-ttu-id="8ffa2-105">(O compilador é responsável por definir esses dois campos adequadamente.)</span><span class="sxs-lookup"><span data-stu-id="8ffa2-105">(The compiler is responsible for setting these two fields appropriately.)</span></span>  
  
 <span data-ttu-id="8ffa2-106">Um compilador deve chamar esse método, emitir o blob de dados para o arquivo PE, definir o `PointerToRawData` campo no IMAGE_DEBUG_DIRECTORY para apontar para os dados emitidos e gravar o IMAGE_DEBUG_DIRECTORY no arquivo PE.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-106">A compiler should call this method, emit the data blob to the PE file, set the `PointerToRawData` field in the IMAGE_DEBUG_DIRECTORY to point to the emitted data, and write the IMAGE_DEBUG_DIRECTORY to the PE file.</span></span> <span data-ttu-id="8ffa2-107">O compilador também deve definir o campo `TimeDateStamp` como igual ao `TimeDateStamp` do arquivo PE que está sendo gerado.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-107">The compiler should also set the `TimeDateStamp` field to equal the `TimeDateStamp` of the PE file being generated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ffa2-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ffa2-108">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ffa2-109">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8ffa2-109">Parameters</span></span>  
 `pIDD`  
 <span data-ttu-id="8ffa2-110">[entrada, saída] Um ponteiro para um IMAGE_DEBUG_DIRECTORY que o gravador de símbolo preencherá.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-110">[in, out] A pointer to an IMAGE_DEBUG_DIRECTORY that the symbol writer will fill out.</span></span>  
  
 `cData`  
 <span data-ttu-id="8ffa2-111">no Um `DWORD` que contém o tamanho dos dados de depuração.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-111">[in] A `DWORD` that contains the size of the debug data.</span></span>  
  
 `pcData`  
 <span data-ttu-id="8ffa2-112">fora Um ponteiro para um `DWORD` que recebe o tamanho do buffer necessário para conter os dados de depuração.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-112">[out] A pointer to a `DWORD` that receives the size of the buffer required to contain the debug data.</span></span>  
  
 `data`  
 <span data-ttu-id="8ffa2-113">fora Um ponteiro para um buffer que é grande o suficiente para manter os dados de depuração para o armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-113">[out] A pointer to a buffer that is large enough to hold the debug data for the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ffa2-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="8ffa2-114">Return Value</span></span>  
 <span data-ttu-id="8ffa2-115">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="8ffa2-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ffa2-116">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="8ffa2-116">Requirements</span></span>  
 <span data-ttu-id="8ffa2-117">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8ffa2-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffa2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ffa2-118">See also</span></span>

- [<span data-ttu-id="8ffa2-119">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="8ffa2-119">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
