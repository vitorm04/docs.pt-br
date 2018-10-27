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
ms.openlocfilehash: 52b0f6b9d3e0ea3d6fe5f14badb8401b1a0c2c63
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187486"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="24c1f-102">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="24c1f-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="24c1f-103">Representa um associador de símbolo para código não gerenciado e estende o [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="24c1f-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24c1f-104">É um risco de segurança para abrir um arquivo de programa (PDB) do banco de dados de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="24c1f-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24c1f-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="24c1f-105">Methods</span></span>  
  
|<span data-ttu-id="24c1f-106">Método</span><span class="sxs-lookup"><span data-stu-id="24c1f-106">Method</span></span>|<span data-ttu-id="24c1f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="24c1f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24c1f-108">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="24c1f-108">GetReaderForFile2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="24c1f-109">Dado uma interface de metadados e um nome de arquivo, retorna a correta [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface que lê os símbolos de depuração associados com o módulo.</span><span class="sxs-lookup"><span data-stu-id="24c1f-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="24c1f-110">Fornece uma pesquisa mais abrangente que o [isymunmanagedbinder:: Getreaderforfile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="24c1f-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="24c1f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="24c1f-111">Requirements</span></span>  
 <span data-ttu-id="24c1f-112">**Cabeçalho:** Corsym, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="24c1f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c1f-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="24c1f-113">See Also</span></span>  
 [<span data-ttu-id="24c1f-114">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="24c1f-114">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="24c1f-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="24c1f-115">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 [<span data-ttu-id="24c1f-116">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="24c1f-116">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)
