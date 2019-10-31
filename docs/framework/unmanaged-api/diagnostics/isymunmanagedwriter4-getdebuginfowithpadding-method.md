---
title: Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 274bf79175bda9e880b1ef3cf8f125a017ad0734
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121665"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="f9513-102">Método ISymUnmanagedWriter4::GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="f9513-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="f9513-103">O funciona da mesma forma que o [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , exceto que a cadeia de caracteres do caminho é preenchida com zeros após o caractere nulo de terminação para tornar os dados da cadeia de caracteres um tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="f9513-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="f9513-104">O preenchimento só será fornecido se o comprimento da cadeia de caracteres do caminho for menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="f9513-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="f9513-105">Isso facilita a gravação de ferramentas que diferenciam arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="f9513-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9513-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9513-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9513-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f9513-107">Parameters</span></span>  
  
|<span data-ttu-id="f9513-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f9513-108">Parameter</span></span>|<span data-ttu-id="f9513-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9513-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="f9513-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f9513-110">Return Value</span></span>  
 <span data-ttu-id="f9513-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="f9513-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9513-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9513-112">Requirements</span></span>  
 <span data-ttu-id="f9513-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f9513-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9513-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9513-114">See also</span></span>

- [<span data-ttu-id="f9513-115">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="f9513-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
