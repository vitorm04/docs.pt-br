---
title: Interface ISymUnmanagedReader
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader
helpviewer_keywords:
- ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: aa3cc15d-058e-4e6f-b03e-39569646ba47
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0782533f773b69eeeb0b89175e5b22c61e822ed9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147206"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="f1333-102">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="f1333-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="f1333-103">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis dentro de um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f1333-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f1333-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="f1333-104">Methods</span></span>  
  
|<span data-ttu-id="f1333-105">Método</span><span class="sxs-lookup"><span data-stu-id="f1333-105">Method</span></span>|<span data-ttu-id="f1333-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1333-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f1333-107">Método GetDocument</span><span class="sxs-lookup"><span data-stu-id="f1333-107">GetDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="f1333-108">Localiza um documento.</span><span class="sxs-lookup"><span data-stu-id="f1333-108">Finds a document.</span></span>|  
|[<span data-ttu-id="f1333-109">Método GetDocuments</span><span class="sxs-lookup"><span data-stu-id="f1333-109">GetDocuments Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="f1333-110">Retorna uma matriz de todos os documentos definidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f1333-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="f1333-111">Método GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="f1333-111">GetDocumentVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="f1333-112">Obtém a versão especificada do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="f1333-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="f1333-113">Método GetGlobalVariables</span><span class="sxs-lookup"><span data-stu-id="f1333-113">GetGlobalVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="f1333-114">Retorna todas as variáveis globais.</span><span class="sxs-lookup"><span data-stu-id="f1333-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="f1333-115">Método GetMethod</span><span class="sxs-lookup"><span data-stu-id="f1333-115">GetMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="f1333-116">Obtém um método de leitor de símbolo, considerando um token de método.</span><span class="sxs-lookup"><span data-stu-id="f1333-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="f1333-117">Método GetMethodByVersion</span><span class="sxs-lookup"><span data-stu-id="f1333-117">GetMethodByVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="f1333-118">Obtém um método de leitor de símbolo, considerando um token de método e um número de versão de editar e copiar.</span><span class="sxs-lookup"><span data-stu-id="f1333-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="f1333-119">Método GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="f1333-119">GetMethodFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="f1333-120">Retorna o método que contém o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="f1333-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="f1333-121">Método GetMethodsFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="f1333-121">GetMethodsFromDocumentPosition Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="f1333-122">Retorna uma matriz dos métodos, cada uma delas contém o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="f1333-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="f1333-123">Método GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="f1333-123">GetMethodVersion Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="f1333-124">Obtém a versão do método.</span><span class="sxs-lookup"><span data-stu-id="f1333-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="f1333-125">Método GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="f1333-125">GetNamespaces Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="f1333-126">Obtém os namespaces definidos no escopo global dentro desse repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f1333-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="f1333-127">Método GetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="f1333-127">GetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="f1333-128">Obtém um atributo personalizado com base em seu nome.</span><span class="sxs-lookup"><span data-stu-id="f1333-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="f1333-129">Método GetSymbolStoreFileName</span><span class="sxs-lookup"><span data-stu-id="f1333-129">GetSymbolStoreFileName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="f1333-130">Fornece o nome de arquivo em disco do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="f1333-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="f1333-131">Método GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="f1333-131">GetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="f1333-132">Retorna o método que foi especificado como o ponto de entrada do usuário para o módulo, se houver.</span><span class="sxs-lookup"><span data-stu-id="f1333-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="f1333-133">Método GetVariables</span><span class="sxs-lookup"><span data-stu-id="f1333-133">GetVariables Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="f1333-134">Retorne a uma variável não local, dado seu pai e o nome.</span><span class="sxs-lookup"><span data-stu-id="f1333-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="f1333-135">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="f1333-135">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-initialize-method.md)|<span data-ttu-id="f1333-136">Inicializa o leitor de símbolo com a interface do importador de metadados que esse leitor será associado, juntamente com o nome de arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="f1333-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="f1333-137">Método ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="f1333-137">ReplaceSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="f1333-138">Substitui o repositório de símbolos existente por um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="f1333-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="f1333-139">Método UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="f1333-139">UpdateSymbolStore Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="f1333-140">Atualiza o repositório de símbolos existente com um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="f1333-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1333-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f1333-141">Requirements</span></span>  
 <span data-ttu-id="f1333-142">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f1333-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1333-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1333-143">See also</span></span>

- [<span data-ttu-id="f1333-144">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="f1333-144">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="f1333-145">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="f1333-145">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)
