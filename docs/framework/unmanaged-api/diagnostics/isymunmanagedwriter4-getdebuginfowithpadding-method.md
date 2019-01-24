---
title: Método ISymUnmanagedWriter4::GetDebugInfoWithPadding
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d669ae15c01a560f2cefb6e361ca32411652fbc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732967"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="a7756-102">Método ISymUnmanagedWriter4::GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="a7756-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="a7756-103">Funciona da mesma maneira [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere nulo de terminação para tornar os dados de cadeia de caracteres de um tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="a7756-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="a7756-104">Preenchimento é dada apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="a7756-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="a7756-105">Isso torna mais fácil escrever ferramentas de que arquivos PE de diferença.</span><span class="sxs-lookup"><span data-stu-id="a7756-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7756-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7756-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7756-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7756-107">Parameters</span></span>  
  
|<span data-ttu-id="a7756-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="a7756-108">Parameter</span></span>|<span data-ttu-id="a7756-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a7756-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="a7756-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a7756-110">Return Value</span></span>  
 <span data-ttu-id="a7756-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="a7756-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7756-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7756-112">Requirements</span></span>  
 <span data-ttu-id="a7756-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a7756-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7756-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7756-114">See also</span></span>
- [<span data-ttu-id="a7756-115">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="a7756-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
