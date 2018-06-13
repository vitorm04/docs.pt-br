---
title: Interface ISymUnmanagedWriter4
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e8478aed662142b9ff4b73f9cb192f8d2306e2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429680"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="5e11e-102">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="5e11e-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="5e11e-103">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="5e11e-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e11e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e11e-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="5e11e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5e11e-105">Methods</span></span>  
 <span data-ttu-id="5e11e-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="5e11e-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="5e11e-107">Método</span><span class="sxs-lookup"><span data-stu-id="5e11e-107">Method</span></span>|<span data-ttu-id="5e11e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e11e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e11e-109">Método GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="5e11e-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="5e11e-110">Funciona da mesma forma [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere null de terminação para tornar os dados de cadeia de caracteres de tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="5e11e-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="5e11e-111">O preenchimento é fornecido apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="5e11e-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="5e11e-112">Isso torna mais fácil escrever ferramentas que arquivos de diferença PE.</span><span class="sxs-lookup"><span data-stu-id="5e11e-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5e11e-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e11e-113">Requirements</span></span>  
 <span data-ttu-id="5e11e-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5e11e-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e11e-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e11e-115">See Also</span></span>  
 [<span data-ttu-id="5e11e-116">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5e11e-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="5e11e-117">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="5e11e-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
