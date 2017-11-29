---
title: "Método ISymUnmanagedWriter::UsingNamespace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.UsingNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b9bfd5ca0c22a9b4da1acb1f93b29150beba865a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="87823-102">Método ISymUnmanagedWriter::UsingNamespace</span><span class="sxs-lookup"><span data-stu-id="87823-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>
<span data-ttu-id="87823-103">Especifica que o nome totalmente qualificado de namespace fornecido está sendo usado dentro do escopo léxico aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="87823-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="87823-104">O namespace será usado em todos os escopos que herdam do escopo aberto no momento.</span><span class="sxs-lookup"><span data-stu-id="87823-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="87823-105">Fechar o escopo atual também vai interromper o uso do namespace.</span><span class="sxs-lookup"><span data-stu-id="87823-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87823-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87823-106">Syntax</span></span>  
  
```  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="87823-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="87823-107">Parameters</span></span>  
 `fullName`  
 <span data-ttu-id="87823-108">[in] Um ponteiro para o nome totalmente qualificado do namespace.</span><span class="sxs-lookup"><span data-stu-id="87823-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87823-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="87823-109">Return Value</span></span>  
 <span data-ttu-id="87823-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="87823-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87823-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="87823-111">Requirements</span></span>  
 <span data-ttu-id="87823-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="87823-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87823-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87823-113">See Also</span></span>  
 [<span data-ttu-id="87823-114">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="87823-114">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
