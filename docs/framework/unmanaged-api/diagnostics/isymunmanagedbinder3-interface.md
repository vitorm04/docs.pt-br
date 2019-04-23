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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157502"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="09878-102">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="09878-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="09878-103">Estende a interface de associador de símbolo.</span><span class="sxs-lookup"><span data-stu-id="09878-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="09878-104">Obtenha essa interface chamando `QueryInterface` em um objeto que implementa o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="09878-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="09878-105">É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="09878-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="09878-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="09878-106">Methods</span></span>  
  
|<span data-ttu-id="09878-107">Método</span><span class="sxs-lookup"><span data-stu-id="09878-107">Method</span></span>|<span data-ttu-id="09878-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="09878-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="09878-109">Método GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="09878-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="09878-110">Permite ao usuário implementar ou fornecer por meio do retorno de chamada ou um `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações de diretório de depuração da memória</span><span class="sxs-lookup"><span data-stu-id="09878-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09878-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09878-111">Requirements</span></span>  
 <span data-ttu-id="09878-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09878-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09878-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09878-113">See also</span></span>

- [<span data-ttu-id="09878-114">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="09878-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="09878-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="09878-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="09878-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="09878-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
