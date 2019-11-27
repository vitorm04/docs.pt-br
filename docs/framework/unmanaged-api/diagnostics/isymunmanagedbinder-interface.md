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
ms.openlocfilehash: f23df98abc5355f0b25d7253b5f2ae808b3446a1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449375"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="f3d4e-102">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="f3d4e-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="f3d4e-103">Representa um fichário de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="f3d4e-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f3d4e-104">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="f3d4e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3d4e-105">{1&gt;Métodos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f3d4e-105">Methods</span></span>  
  
|<span data-ttu-id="f3d4e-106">Método</span><span class="sxs-lookup"><span data-stu-id="f3d4e-106">Method</span></span>|<span data-ttu-id="f3d4e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f3d4e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3d4e-108">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="f3d4e-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="f3d4e-109">Dada uma interface de metadados e um nome de arquivo, retorna a estrutura [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="f3d4e-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="f3d4e-110">Método GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="f3d4e-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="f3d4e-111">Dada uma interface de metadados e um fluxo que contém o armazenamento de símbolo, retorna a estrutura [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração do repositório de símbolos fornecido.</span><span class="sxs-lookup"><span data-stu-id="f3d4e-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f3d4e-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f3d4e-112">Requirements</span></span>  
 <span data-ttu-id="f3d4e-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f3d4e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3d4e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3d4e-114">See also</span></span>

- [<span data-ttu-id="f3d4e-115">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="f3d4e-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f3d4e-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="f3d4e-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="f3d4e-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="f3d4e-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
