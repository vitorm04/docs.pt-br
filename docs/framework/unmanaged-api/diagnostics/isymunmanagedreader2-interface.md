---
title: Interface ISymUnmanagedReader2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08695c4e5df6aaa63bedecf68b741302e5ddd8e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524931"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="53f5a-102">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="53f5a-102">ISymUnmanagedReader2 Interface</span></span>
<span data-ttu-id="53f5a-103">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis dentro de um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="53f5a-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="53f5a-104">Essa interface estende o [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="53f5a-104">This interface extends the [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="53f5a-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="53f5a-105">Methods</span></span>  
  
|<span data-ttu-id="53f5a-106">Método</span><span class="sxs-lookup"><span data-stu-id="53f5a-106">Method</span></span>|<span data-ttu-id="53f5a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="53f5a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="53f5a-108">Método GetMethodByVersionPreRemap</span><span class="sxs-lookup"><span data-stu-id="53f5a-108">GetMethodByVersionPreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="53f5a-109">Obter um método de leitor de símbolo, considerando um token de método e um número de versão de editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="53f5a-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="53f5a-110">Método GetMethodsInDocument</span><span class="sxs-lookup"><span data-stu-id="53f5a-110">GetMethodsInDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="53f5a-111">Obtém todos os métodos que tem informações de linha no documento fornecido.</span><span class="sxs-lookup"><span data-stu-id="53f5a-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="53f5a-112">Método GetSymAttributePreRemap</span><span class="sxs-lookup"><span data-stu-id="53f5a-112">GetSymAttributePreRemap Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="53f5a-113">Obtém um atributo personalizado com base em seu nome.</span><span class="sxs-lookup"><span data-stu-id="53f5a-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="53f5a-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="53f5a-114">Requirements</span></span>  
 <span data-ttu-id="53f5a-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="53f5a-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53f5a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="53f5a-116">See also</span></span>
- [<span data-ttu-id="53f5a-117">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="53f5a-117">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="53f5a-118">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="53f5a-118">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
