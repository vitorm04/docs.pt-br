---
title: Método ISymUnmanagedWriter::CloseMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseMethod
helpviewer_keywords:
- ISymUnmanagedWriter::CloseMethod method [.NET Framework debugging]
- CloseMethod method [.NET Framework debugging]
ms.assetid: b8025e04-f0e5-40c8-849c-8cd51323420e
topic_type:
- apiref
ms.openlocfilehash: a6a6aa937078ed0627688a4eed3d9142a2e6e0ac
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428098"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="f487e-102">Método ISymUnmanagedWriter::CloseMethod</span><span class="sxs-lookup"><span data-stu-id="f487e-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="f487e-103">Fecha o método atual.</span><span class="sxs-lookup"><span data-stu-id="f487e-103">Closes the current method.</span></span> <span data-ttu-id="f487e-104">Depois que um método é fechado, nenhum símbolo pode ser definido dentro dele.</span><span class="sxs-lookup"><span data-stu-id="f487e-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f487e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f487e-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f487e-106">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="f487e-106">Return Value</span></span>  
 <span data-ttu-id="f487e-107">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="f487e-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f487e-108">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="f487e-108">Requirements</span></span>  
 <span data-ttu-id="f487e-109">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f487e-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f487e-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f487e-110">See also</span></span>

- [<span data-ttu-id="f487e-111">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="f487e-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
- [<span data-ttu-id="f487e-112">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="f487e-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
