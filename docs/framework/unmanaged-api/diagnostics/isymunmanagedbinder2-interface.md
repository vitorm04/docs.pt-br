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
ms.openlocfilehash: f6155eb777b5071ff522af4f27d5fb2d73aa25ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501827"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="3f79e-102">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="3f79e-102">ISymUnmanagedBinder2 Interface</span></span>
<span data-ttu-id="3f79e-103">Representa um fichário de símbolo para código não gerenciado e estende a interface [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3f79e-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3f79e-104">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="3f79e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f79e-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="3f79e-105">Methods</span></span>  
  
|<span data-ttu-id="3f79e-106">Método</span><span class="sxs-lookup"><span data-stu-id="3f79e-106">Method</span></span>|<span data-ttu-id="3f79e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3f79e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f79e-108">Método GetReaderForFile2</span><span class="sxs-lookup"><span data-stu-id="3f79e-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="3f79e-109">Dada uma interface de metadados e um nome de arquivo, retorna a interface [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="3f79e-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="3f79e-110">Fornece uma pesquisa mais abrangente do que o método [ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3f79e-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f79e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3f79e-111">Requirements</span></span>  
 <span data-ttu-id="3f79e-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3f79e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f79e-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="3f79e-113">See also</span></span>

- [<span data-ttu-id="3f79e-114">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="3f79e-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="3f79e-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="3f79e-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="3f79e-116">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="3f79e-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
