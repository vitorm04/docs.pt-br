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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfd8e8fc419809a3a490639ada1c533f286fe8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157502"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="a2f49-102">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="a2f49-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="a2f49-103">Estende a interface de associador de símbolo.</span><span class="sxs-lookup"><span data-stu-id="a2f49-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="a2f49-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="a2f49-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a2f49-105">É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="a2f49-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2f49-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="a2f49-106">Methods</span></span>  
  
|<span data-ttu-id="a2f49-107">Método</span><span class="sxs-lookup"><span data-stu-id="a2f49-107">Method</span></span>|<span data-ttu-id="a2f49-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2f49-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2f49-109">Método GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="a2f49-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="a2f49-110">Permite ao usuário implementar ou fornecer por meio do retorno de chamada ou um `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações de diretório de depuração da memória</span><span class="sxs-lookup"><span data-stu-id="a2f49-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a2f49-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a2f49-111">Requirements</span></span>  
 <span data-ttu-id="a2f49-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a2f49-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f49-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2f49-113">See also</span></span>

- [<span data-ttu-id="a2f49-114">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="a2f49-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="a2f49-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="a2f49-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="a2f49-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="a2f49-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
