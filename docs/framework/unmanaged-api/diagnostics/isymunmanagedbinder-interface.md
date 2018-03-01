---
title: Interface ISymUnmanagedBinder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedBinder
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder
helpviewer_keywords:
- ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79d3758f57976d08d4599de500e2e12e4d67cb4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="393f8-102">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="393f8-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="393f8-103">Representa um associador de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="393f8-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="393f8-104">É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="393f8-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="393f8-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="393f8-105">Methods</span></span>  
  
|<span data-ttu-id="393f8-106">Método</span><span class="sxs-lookup"><span data-stu-id="393f8-106">Method</span></span>|<span data-ttu-id="393f8-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="393f8-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="393f8-108">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="393f8-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="393f8-109">Dado uma interface de metadados e um nome de arquivo, retorna o correto [ISymUnmanagedReader](isymunmanagedreader-interface.md) estrutura que lerá os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="393f8-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="393f8-110">Método GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="393f8-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="393f8-111">Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna o correto [ISymUnmanagedReader](isymunmanagedreader-interface.md) símbolos de estrutura que lerá a depuração do armazenamento de símbolo dado.</span><span class="sxs-lookup"><span data-stu-id="393f8-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="393f8-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="393f8-112">Requirements</span></span>  
 <span data-ttu-id="393f8-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="393f8-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393f8-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="393f8-114">See Also</span></span>  
 [<span data-ttu-id="393f8-115">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="393f8-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="393f8-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="393f8-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="393f8-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="393f8-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
