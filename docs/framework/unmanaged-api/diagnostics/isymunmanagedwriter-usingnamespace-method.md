---
title: Método ISymUnmanagedWriter::UsingNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d0739cc38d1f12967f0daef2d6828e04a256ade6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201839"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="43036-102">Método ISymUnmanagedWriter::UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="43036-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="43036-103">Especifica que o nome totalmente qualificado do namespace fornecido está sendo usado dentro do escopo léxico aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="43036-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="43036-104">O namespace será usado em todos os escopos que herdam do escopo aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="43036-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="43036-105">Fechar o escopo atual também vai interromper o uso do namespace.</span><span class="sxs-lookup"><span data-stu-id="43036-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43036-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43036-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43036-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="43036-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="43036-108">[in] Um ponteiro para o nome totalmente qualificado do namespace.</span><span class="sxs-lookup"><span data-stu-id="43036-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43036-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="43036-109">Return Value</span></span>  
 <span data-ttu-id="43036-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="43036-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43036-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="43036-111">Requirements</span></span>  
 <span data-ttu-id="43036-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="43036-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43036-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43036-113">See also</span></span>

- [<span data-ttu-id="43036-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="43036-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
