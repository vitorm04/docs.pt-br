---
title: Interface ISymUnmanagedBinder3
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder3
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder3 Interface
helpviewer_keywords: ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: df5cd6d4015fad1baf98909ee9cc923cd9bce05e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="f3843-102">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="f3843-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="f3843-103">Estende a interface de associador de símbolo.</span><span class="sxs-lookup"><span data-stu-id="f3843-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="f3843-104">Obter essa interface chamando `QueryInterface` em um objeto que implementa o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="f3843-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f3843-105">É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="f3843-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3843-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="f3843-106">Methods</span></span>  
  
|<span data-ttu-id="f3843-107">Método</span><span class="sxs-lookup"><span data-stu-id="f3843-107">Method</span></span>|<span data-ttu-id="f3843-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3843-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3843-109">Método GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="f3843-109">GetReaderFromCallback Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="f3843-110">Permite que o usuário implementa ou fornecer por meio do retorno de chamada ou uma `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações de diretório de depuração da memória</span><span class="sxs-lookup"><span data-stu-id="f3843-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3843-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f3843-111">Requirements</span></span>  
 <span data-ttu-id="f3843-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f3843-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3843-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3843-113">See Also</span></span>  
 [<span data-ttu-id="f3843-114">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="f3843-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="f3843-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="f3843-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="f3843-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="f3843-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
