---
title: Interface ISymUnmanagedBinder
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6d91f68ac737ce28cdbef926119bb3711bc1096
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940056"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="5b797-102">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="5b797-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="5b797-103">Representa um associador de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5b797-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5b797-104">É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="5b797-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5b797-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5b797-105">Methods</span></span>  
  
|<span data-ttu-id="5b797-106">Método</span><span class="sxs-lookup"><span data-stu-id="5b797-106">Method</span></span>|<span data-ttu-id="5b797-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5b797-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5b797-108">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="5b797-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="5b797-109">Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) estrutura que lerá os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="5b797-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="5b797-110">Método GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="5b797-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="5b797-111">Dado uma interface de metadados e um fluxo que contém o repositório de símbolos, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) símbolos de estrutura que será lido a depuração do armazenamento de símbolo dado.</span><span class="sxs-lookup"><span data-stu-id="5b797-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5b797-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b797-112">Requirements</span></span>  
 <span data-ttu-id="5b797-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b797-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b797-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b797-114">See also</span></span>

- [<span data-ttu-id="5b797-115">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5b797-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5b797-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="5b797-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="5b797-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="5b797-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
