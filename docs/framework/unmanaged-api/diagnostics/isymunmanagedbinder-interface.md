---
title: Interface ISymUnmanagedBinder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder
helpviewer_keywords: ISymUnmanagedBinder interface [.NET Framework debugging]
ms.assetid: b22fbe19-b30f-4696-8175-e6b91da9edab
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5061ce28c4a09f445267c99420bf1942d99076bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="4d200-102">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="4d200-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="4d200-103">Representa um associador de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="4d200-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4d200-104">É um risco de segurança para abrir um arquivo de programa (PDB) de banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="4d200-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d200-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="4d200-105">Methods</span></span>  
  
|<span data-ttu-id="4d200-106">Método</span><span class="sxs-lookup"><span data-stu-id="4d200-106">Method</span></span>|<span data-ttu-id="4d200-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d200-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d200-108">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="4d200-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="4d200-109">Dado uma interface de metadados e um nome de arquivo, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> estrutura que lerá os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="4d200-109">Given a metadata interface and a file name, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="4d200-110">Método GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="4d200-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="4d200-111">Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna o correto <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> símbolos de estrutura que lerá a depuração do armazenamento de símbolo dado.</span><span class="sxs-lookup"><span data-stu-id="4d200-111">Given a metadata interface and a stream that contains the symbol store, returns the correct <<!--zz xref:ISymUnmanagedReader --> `ISymUnmanagedReader`> structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4d200-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4d200-112">Requirements</span></span>  
 <span data-ttu-id="4d200-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="4d200-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d200-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d200-114">See Also</span></span>  
 [<span data-ttu-id="4d200-115">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4d200-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="4d200-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="4d200-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 [<span data-ttu-id="4d200-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="4d200-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
