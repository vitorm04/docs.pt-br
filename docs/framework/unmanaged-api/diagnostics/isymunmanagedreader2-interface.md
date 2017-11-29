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
ms.openlocfilehash: b23e166249659b94d454070c01c003495d1018a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="ccee0-102">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="ccee0-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="ccee0-103">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="ccee0-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="ccee0-104">Essa interface estende o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="ccee0-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccee0-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="ccee0-105">Methods</span></span>  
  
|<span data-ttu-id="ccee0-106">Método</span><span class="sxs-lookup"><span data-stu-id="ccee0-106">Method</span></span>|<span data-ttu-id="ccee0-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ccee0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccee0-108">Método GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="ccee0-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="ccee0-109">Obter um método de leitor de símbolo, considerando um token de método e um número de versão de edit-and-continue.</span><span class="sxs-lookup"><span data-stu-id="ccee0-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="ccee0-110">Método GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="ccee0-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="ccee0-111">Obtém cada método que tem informações de linha do documento fornecido.</span><span class="sxs-lookup"><span data-stu-id="ccee0-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="ccee0-112">Método GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="ccee0-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="ccee0-113">Obtém um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="ccee0-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ccee0-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ccee0-114">Requirements</span></span>  
 <span data-ttu-id="ccee0-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ccee0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccee0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ccee0-116">See Also</span></span>  
 [<span data-ttu-id="ccee0-117">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ccee0-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="ccee0-118">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="ccee0-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
