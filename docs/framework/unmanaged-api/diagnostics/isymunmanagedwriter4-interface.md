---
title: Interface ISymUnmanagedWriter4
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: a656777461c50b5a1593917278eb54abda982dc2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134564"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="46c14-102">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="46c14-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="46c14-103">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="46c14-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46c14-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46c14-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="46c14-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="46c14-105">Methods</span></span>  
 <span data-ttu-id="46c14-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="46c14-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="46c14-107">Método</span><span class="sxs-lookup"><span data-stu-id="46c14-107">Method</span></span>|<span data-ttu-id="46c14-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="46c14-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46c14-109">Método GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="46c14-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="46c14-110">O funciona da mesma forma que o [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , exceto que a cadeia de caracteres do caminho é preenchida com zeros após o caractere nulo de terminação para tornar os dados da cadeia de caracteres um tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="46c14-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="46c14-111">O preenchimento só será fornecido se o comprimento da cadeia de caracteres do caminho for menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="46c14-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="46c14-112">Isso facilita a gravação de ferramentas que diferenciam arquivos PE.</span><span class="sxs-lookup"><span data-stu-id="46c14-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46c14-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46c14-113">Requirements</span></span>  
 <span data-ttu-id="46c14-114">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="46c14-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46c14-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46c14-115">See also</span></span>

- [<span data-ttu-id="46c14-116">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="46c14-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="46c14-117">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="46c14-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
