---
title: Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: cfc6c22558cee780823c8cca0c36b883147e9496
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614637"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="7f2b0-102">Método ISymUnmanagedWriter4::GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="7f2b0-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="7f2b0-103">O funciona da mesma forma que o [método GetDebugInfo](isymunmanagedwriter-getdebuginfo-method.md) , exceto pelo fato de que a cadeia de caracteres de caminho é preenchida com zeros após o caractere nulo de terminação para tornar os dados da cadeia de caracteres um tamanho fixo `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="7f2b0-103">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="7f2b0-104">O preenchimento só será fornecido se o comprimento da cadeia de caracteres do caminho for menor que `MAX_PATH` .</span><span class="sxs-lookup"><span data-stu-id="7f2b0-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="7f2b0-105">Isso facilita a gravação de ferramentas que diferenciam arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="7f2b0-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f2b0-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f2b0-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f2b0-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f2b0-107">Parameters</span></span>  
  
|<span data-ttu-id="7f2b0-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="7f2b0-108">Parameter</span></span>|<span data-ttu-id="7f2b0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="7f2b0-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="7f2b0-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7f2b0-110">Return Value</span></span>  
 <span data-ttu-id="7f2b0-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="7f2b0-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f2b0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f2b0-112">Requirements</span></span>  
 <span data-ttu-id="7f2b0-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="7f2b0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2b0-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="7f2b0-114">See also</span></span>

- [<span data-ttu-id="7f2b0-115">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="7f2b0-115">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
