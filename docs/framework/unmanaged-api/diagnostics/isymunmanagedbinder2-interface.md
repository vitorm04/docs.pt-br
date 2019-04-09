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
ms.openlocfilehash: 38de9fa878db18222d2666ba86420ca856e4b121
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59199109"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="92f71-102">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="92f71-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="92f71-103">Representa um associador de símbolo para código não gerenciado e estende o [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="92f71-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="92f71-104">É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="92f71-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92f71-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="92f71-105">Methods</span></span>  
  
|<span data-ttu-id="92f71-106">Método</span><span class="sxs-lookup"><span data-stu-id="92f71-106">Method</span></span>|<span data-ttu-id="92f71-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="92f71-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92f71-108">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="92f71-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="92f71-109">Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface que lê os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="92f71-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="92f71-110">Fornece uma pesquisa mais abrangente que o [isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="92f71-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="92f71-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92f71-111">Requirements</span></span>  
 <span data-ttu-id="92f71-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="92f71-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f71-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92f71-113">See also</span></span>

- [<span data-ttu-id="92f71-114">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="92f71-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="92f71-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="92f71-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)
- [<span data-ttu-id="92f71-116">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="92f71-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
