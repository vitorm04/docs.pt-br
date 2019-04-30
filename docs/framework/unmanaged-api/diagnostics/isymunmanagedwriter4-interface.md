---
title: Interface ISymUnmanagedWriter4
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5732cc08512df25a14cc8ea9dcaa03c56207dde
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962325"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="0d654-102">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="0d654-102">ISymUnmanagedWriter4 Interface</span></span>
<span data-ttu-id="0d654-103">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="0d654-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d654-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0d654-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="0d654-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="0d654-105">Methods</span></span>  
 <span data-ttu-id="0d654-106">Essa interface contém os seguintes métodos:</span><span class="sxs-lookup"><span data-stu-id="0d654-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="0d654-107">Método</span><span class="sxs-lookup"><span data-stu-id="0d654-107">Method</span></span>|<span data-ttu-id="0d654-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d654-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d654-109">Método GetDebugInfoWithPadding</span><span class="sxs-lookup"><span data-stu-id="0d654-109">GetDebugInfoWithPadding Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="0d654-110">Funciona da mesma maneira [método GetDebugInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) , exceto que a cadeia de caracteres de caminho é preenchida com zeros após o caractere nulo de terminação para tornar os dados de cadeia de caracteres de um tamanho fixo de `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0d654-110">Functions the same as [GetDebugInfo Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="0d654-111">Preenchimento é dada apenas se o comprimento da cadeia de caracteres de caminho em si é menor que `MAX_PATH`.</span><span class="sxs-lookup"><span data-stu-id="0d654-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="0d654-112">Isso torna mais fácil escrever ferramentas de que arquivos PE de diferença.</span><span class="sxs-lookup"><span data-stu-id="0d654-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d654-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0d654-113">Requirements</span></span>  
 <span data-ttu-id="0d654-114">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0d654-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d654-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d654-115">See also</span></span>

- [<span data-ttu-id="0d654-116">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="0d654-116">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="0d654-117">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="0d654-117">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
