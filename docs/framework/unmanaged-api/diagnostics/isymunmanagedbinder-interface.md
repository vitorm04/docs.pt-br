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
ms.openlocfilehash: f4f925282d65cd9cbc8eb1c8825f358602de68ed
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441689"
---
# <a name="isymunmanagedbinder-interface"></a><span data-ttu-id="5300d-102">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="5300d-102">ISymUnmanagedBinder Interface</span></span>
<span data-ttu-id="5300d-103">Representa um fichário de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="5300d-103">Represents a symbol binder for unmanaged code.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5300d-104">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="5300d-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5300d-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="5300d-105">Methods</span></span>  
  
|<span data-ttu-id="5300d-106">Método</span><span class="sxs-lookup"><span data-stu-id="5300d-106">Method</span></span>|<span data-ttu-id="5300d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5300d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5300d-108">Método GetReaderForFile</span><span class="sxs-lookup"><span data-stu-id="5300d-108">GetReaderForFile Method</span></span>](isymunmanagedbinder-getreaderforfile-method.md)|<span data-ttu-id="5300d-109">Dada uma interface de metadados e um nome de arquivo, retorna a estrutura [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração associados ao módulo.</span><span class="sxs-lookup"><span data-stu-id="5300d-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols associated with the module.</span></span>|  
|[<span data-ttu-id="5300d-110">Método GetReaderFromStream</span><span class="sxs-lookup"><span data-stu-id="5300d-110">GetReaderFromStream Method</span></span>](isymunmanagedbinder-getreaderfromstream-method.md)|<span data-ttu-id="5300d-111">Dada uma interface de metadados e um fluxo que contém o armazenamento de símbolo, retorna a estrutura [ISymUnmanagedReader](isymunmanagedreader-interface.md) correta que lerá os símbolos de depuração do repositório de símbolos fornecido.</span><span class="sxs-lookup"><span data-stu-id="5300d-111">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="5300d-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5300d-112">Requirements</span></span>  
 <span data-ttu-id="5300d-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="5300d-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5300d-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="5300d-114">See also</span></span>

- [<span data-ttu-id="5300d-115">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5300d-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="5300d-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="5300d-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
- [<span data-ttu-id="5300d-117">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="5300d-117">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
