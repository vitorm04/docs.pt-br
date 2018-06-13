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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 71be697a8a1decd9b5f780d047c3dbb397e351d0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426881"
---
# <a name="isymunmanagedwriterclosemethod-method"></a><span data-ttu-id="27fca-102">Método ISymUnmanagedWriter::CloseMethod</span><span class="sxs-lookup"><span data-stu-id="27fca-102">ISymUnmanagedWriter::CloseMethod Method</span></span>
<span data-ttu-id="27fca-103">Fecha o método atual.</span><span class="sxs-lookup"><span data-stu-id="27fca-103">Closes the current method.</span></span> <span data-ttu-id="27fca-104">Quando um método é fechado, não mais símbolos podem ser definidos dentro dele.</span><span class="sxs-lookup"><span data-stu-id="27fca-104">Once a method is closed, no more symbols can be defined within it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27fca-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27fca-105">Syntax</span></span>  
  
```  
HRESULT CloseMethod();  
```  
  
## <a name="return-value"></a><span data-ttu-id="27fca-106">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="27fca-106">Return Value</span></span>  
 <span data-ttu-id="27fca-107">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="27fca-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27fca-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27fca-108">Requirements</span></span>  
 <span data-ttu-id="27fca-109">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27fca-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27fca-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27fca-110">See Also</span></span>  
 [<span data-ttu-id="27fca-111">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="27fca-111">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 [<span data-ttu-id="27fca-112">Método OpenMethod</span><span class="sxs-lookup"><span data-stu-id="27fca-112">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
