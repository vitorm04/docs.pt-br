---
title: Interface ISymUnmanagedBinder2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c9fbb8364fb967e739eb9807b26cbc65f0ebec1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944186"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="7cc67-102">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="7cc67-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="7cc67-103">Representa um fichário de símbolo para código não gerenciado e estende a interface [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="7cc67-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7cc67-104">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="7cc67-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7cc67-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="7cc67-105">Methods</span></span>  
  
|<span data-ttu-id="7cc67-106">Método</span><span class="sxs-lookup"><span data-stu-id="7cc67-106">Method</span></span>|<span data-ttu-id="7cc67-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cc67-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7cc67-108">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="7cc67-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="7cc67-109">Dada uma interface de metadados e um nome de arquivo, retorna a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="7cc67-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="7cc67-110">Fornece uma pesquisa mais abrangente do que o método [ISymUnmanagedBinder:: GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7cc67-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cc67-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7cc67-111">Requirements</span></span>  
 <span data-ttu-id="7cc67-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7cc67-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cc67-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cc67-113">See also</span></span>

- [<span data-ttu-id="7cc67-114">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="7cc67-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="7cc67-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="7cc67-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="7cc67-116">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="7cc67-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
