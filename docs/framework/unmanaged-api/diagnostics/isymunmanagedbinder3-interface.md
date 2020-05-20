---
title: Interface ISymUnmanagedBinder3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3 Interface
helpviewer_keywords:
- ISymUnmanagedBinder3 interface [.NET Framework debugging]
ms.assetid: 37527a84-4b03-4f08-8135-94d898599089
topic_type:
- apiref
ms.openlocfilehash: 5a26de2a8f5439b7c81560927c991d449e57b76c
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441585"
---
# <a name="isymunmanagedbinder3-interface"></a><span data-ttu-id="ceadd-102">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="ceadd-102">ISymUnmanagedBinder3 Interface</span></span>
<span data-ttu-id="ceadd-103">Estende a interface do fichário de símbolos.</span><span class="sxs-lookup"><span data-stu-id="ceadd-103">Extends the symbol binder interface.</span></span> <span data-ttu-id="ceadd-104">Obtenha essa interface chamando `QueryInterface` um objeto que implementa a `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="ceadd-104">Obtain this interface by calling `QueryInterface` on an object that implements the `ISymUnmanagedBinder` interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ceadd-105">É um risco de segurança abrir um arquivo de banco de dados do programa (PDB) de uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="ceadd-105">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ceadd-106">Métodos</span><span class="sxs-lookup"><span data-stu-id="ceadd-106">Methods</span></span>  
  
|<span data-ttu-id="ceadd-107">Método</span><span class="sxs-lookup"><span data-stu-id="ceadd-107">Method</span></span>|<span data-ttu-id="ceadd-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ceadd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ceadd-109">Método GetReaderFromCallback</span><span class="sxs-lookup"><span data-stu-id="ceadd-109">GetReaderFromCallback Method</span></span>](isymunmanagedbinder3-getreaderfromcallback-method.md)|<span data-ttu-id="ceadd-110">Permite que o usuário implemente ou forneça por meio de um retorno de chamada `IID_IDiaReadExeAtRVACallback` ou `IID_IDiaReadExeAtOffsetCallback` para obter as informações do diretório de depuração da memória</span><span class="sxs-lookup"><span data-stu-id="ceadd-110">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the Debug directory information from memory</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ceadd-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ceadd-111">Requirements</span></span>  
 <span data-ttu-id="ceadd-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ceadd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceadd-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="ceadd-113">See also</span></span>

- [<span data-ttu-id="ceadd-114">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ceadd-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="ceadd-115">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="ceadd-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="ceadd-116">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="ceadd-116">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)
