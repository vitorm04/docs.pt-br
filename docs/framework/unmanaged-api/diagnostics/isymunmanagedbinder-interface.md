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
ms.openlocfilehash: e2160ad4174d9cdfe6e27d2ba7f4748bd473a5f9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944228"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="ea2f0-102">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="ea2f0-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="ea2f0-103">Representa um fichário de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ea2f0-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ea2f0-104">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="ea2f0-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ea2f0-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ea2f0-105">Methods</span></span>  
  
|<span data-ttu-id="ea2f0-106">Método</span><span class="sxs-lookup"><span data-stu-id="ea2f0-106">Method</span></span>|<span data-ttu-id="ea2f0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea2f0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ea2f0-108">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="ea2f0-108">GetReaderForFile Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="ea2f0-109">Dada uma interface de metadados e um nome de arquivo, retorna a estrutura [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="ea2f0-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="ea2f0-110">Método GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="ea2f0-110">GetReaderFromStream Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="ea2f0-111">Dada uma interface de metadados e um fluxo que contém o armazenamento de símbolo, retorna a estrutura [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração do repositório de símbolos fornecido.</span><span class="sxs-lookup"><span data-stu-id="ea2f0-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea2f0-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ea2f0-112">Requirements</span></span>  
 <span data-ttu-id="ea2f0-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ea2f0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea2f0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea2f0-114">See also</span></span>

- [<span data-ttu-id="ea2f0-115">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ea2f0-115">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ea2f0-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="ea2f0-116">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="ea2f0-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="ea2f0-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
