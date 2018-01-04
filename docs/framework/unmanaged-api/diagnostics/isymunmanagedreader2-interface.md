---
title: Interface ISymUnmanagedReader2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader2
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader2
helpviewer_keywords: ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 93f4b88d891d7b5c1d92006276a290841372aad7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="dc2cc-102">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="dc2cc-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="dc2cc-103">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="dc2cc-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="dc2cc-104">Essa interface estende o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="dc2cc-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dc2cc-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="dc2cc-105">Methods</span></span>  
  
|<span data-ttu-id="dc2cc-106">Método</span><span class="sxs-lookup"><span data-stu-id="dc2cc-106">Method</span></span>|<span data-ttu-id="dc2cc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dc2cc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dc2cc-108">Método GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="dc2cc-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="dc2cc-109">Obter um método de leitor de símbolo, considerando um token de método e um número de versão de edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="dc2cc-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="dc2cc-110">Método GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="dc2cc-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="dc2cc-111">Obtém cada método que tem informações de linha do documento fornecido.</span><span class="sxs-lookup"><span data-stu-id="dc2cc-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="dc2cc-112">Método GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="dc2cc-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="dc2cc-113">Obtém um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="dc2cc-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dc2cc-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dc2cc-114">Requirements</span></span>  
 <span data-ttu-id="dc2cc-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dc2cc-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc2cc-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc2cc-116">See Also</span></span>  
 [<span data-ttu-id="dc2cc-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="dc2cc-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="dc2cc-118">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="dc2cc-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
