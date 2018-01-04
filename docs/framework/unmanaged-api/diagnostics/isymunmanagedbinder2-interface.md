---
title: Interface ISymUnmanagedBinder2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder2 Interface
helpviewer_keywords: ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fff140f6848b91e811ef4546a3e8fd50eb61e05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="7ce16-102">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="7ce16-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="7ce16-103">Representa um associador de símbolo para código não gerenciado e estende o [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="7ce16-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7ce16-104">É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="7ce16-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ce16-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7ce16-105">Methods</span></span>  
  
|<span data-ttu-id="7ce16-106">Método</span><span class="sxs-lookup"><span data-stu-id="7ce16-106">Method</span></span>|<span data-ttu-id="7ce16-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ce16-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ce16-108">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="7ce16-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="7ce16-109">Dado uma interface de metadados e um nome de arquivo, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface que lerá os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="7ce16-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="7ce16-110">Fornece uma pesquisa mais ampla que o [Isymunmanagedbinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="7ce16-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ce16-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7ce16-111">Requirements</span></span>  
 <span data-ttu-id="7ce16-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7ce16-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce16-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ce16-113">See Also</span></span>  
 [<span data-ttu-id="7ce16-114">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7ce16-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="7ce16-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="7ce16-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="7ce16-116">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="7ce16-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
