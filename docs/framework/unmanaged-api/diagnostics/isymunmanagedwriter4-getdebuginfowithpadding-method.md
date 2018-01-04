---
title: "Método ISymUnmanagedWriter4::GetDebugInfoWithPadding"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f85486370d567ceb1506c41f6aa7c4f3a1929941
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="1779c-102">Método ISymUnmanagedWriter4::GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="1779c-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>
<span data-ttu-id="1779c-103">Funciona da mesma forma [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere null de terminação para tornar os dados de cadeia de caracteres de tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="1779c-103">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="1779c-104">O preenchimento é fornecido apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="1779c-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="1779c-105">Isso torna mais fácil escrever ferramentas que arquivos de diferença PE.</span><span class="sxs-lookup"><span data-stu-id="1779c-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1779c-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1779c-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1779c-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1779c-107">Parameters</span></span>  
  
|<span data-ttu-id="1779c-108">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="1779c-108">Parameter</span></span>|<span data-ttu-id="1779c-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="1779c-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="1779c-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1779c-110">Return Value</span></span>  
 <span data-ttu-id="1779c-111">Retorna `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="1779c-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1779c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1779c-112">Requirements</span></span>  
 <span data-ttu-id="1779c-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1779c-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1779c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1779c-114">See Also</span></span>  
 [<span data-ttu-id="1779c-115">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="1779c-115">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)
