---
title: Interface ISymUnmanagedBinder3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: e4a415b21e3980e7603319d7acbb3831462fac9e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449289"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="4a1de-102">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="4a1de-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="4a1de-103">Estende a interface do fichário de símbolos.</span><span class="sxs-lookup"><span data-stu-id="4a1de-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="4a1de-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa a interface `ISymUnmanagedBinder`.</span><span class="sxs-lookup"><span data-stu-id="4a1de-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4a1de-105">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="4a1de-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4a1de-106">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4a1de-106">Methods</span></span>  
  
|<span data-ttu-id="4a1de-107">Método</span><span class="sxs-lookup"><span data-stu-id="4a1de-107">Method</span></span>|<span data-ttu-id="4a1de-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a1de-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4a1de-109">Método GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="4a1de-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="4a1de-110">Permite que o usuário implemente ou forneça por meio do retorno de chamada um `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações do diretório de depuração da memória</span><span class="sxs-lookup"><span data-stu-id="4a1de-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4a1de-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="4a1de-111">Requirements</span></span>  
 <span data-ttu-id="4a1de-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4a1de-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a1de-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a1de-113">See also</span></span>

- [<span data-ttu-id="4a1de-114">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4a1de-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="4a1de-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="4a1de-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="4a1de-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="4a1de-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
