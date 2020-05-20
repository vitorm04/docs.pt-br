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
ms.openlocfilehash: b372021fcda39d9973d96a9c39e93e38617887a6
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615456"
---
# <a name="isymunmanagedreader-interface"></a><span data-ttu-id="2567a-102">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="2567a-102">ISymUnmanagedReader Interface</span></span>
<span data-ttu-id="2567a-103">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="2567a-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2567a-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="2567a-104">Methods</span></span>  
  
|<span data-ttu-id="2567a-105">Método</span><span class="sxs-lookup"><span data-stu-id="2567a-105">Method</span></span>|<span data-ttu-id="2567a-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="2567a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2567a-107">Método GetDocument</span><span class="sxs-lookup"><span data-stu-id="2567a-107">GetDocument Method</span></span>](isymunmanagedreader-getdocument-method.md)|<span data-ttu-id="2567a-108">Localiza um documento.</span><span class="sxs-lookup"><span data-stu-id="2567a-108">Finds a document.</span></span>|  
|[<span data-ttu-id="2567a-109">Método GetDocuments</span><span class="sxs-lookup"><span data-stu-id="2567a-109">GetDocuments Method</span></span>](isymunmanagedreader-getdocuments-method.md)|<span data-ttu-id="2567a-110">Retorna uma matriz de todos os documentos definidos no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="2567a-110">Returns an array of all the documents defined in the symbol store.</span></span>|  
|[<span data-ttu-id="2567a-111">Método GetDocumentVersion</span><span class="sxs-lookup"><span data-stu-id="2567a-111">GetDocumentVersion Method</span></span>](isymunmanagedreader-getdocumentversion-method.md)|<span data-ttu-id="2567a-112">Obtém a versão especificada do documento especificado.</span><span class="sxs-lookup"><span data-stu-id="2567a-112">Gets the specified version of the specified document.</span></span>|  
|[<span data-ttu-id="2567a-113">Método GetGlobalVariables</span><span class="sxs-lookup"><span data-stu-id="2567a-113">GetGlobalVariables Method</span></span>](isymunmanagedreader-getglobalvariables-method.md)|<span data-ttu-id="2567a-114">Retorna todas as variáveis globais.</span><span class="sxs-lookup"><span data-stu-id="2567a-114">Returns all global variables.</span></span>|  
|[<span data-ttu-id="2567a-115">Método GetMethod</span><span class="sxs-lookup"><span data-stu-id="2567a-115">GetMethod Method</span></span>](isymunmanagedreader-getmethod-method.md)|<span data-ttu-id="2567a-116">Obtém um método de leitor de símbolo, dado um token de método.</span><span class="sxs-lookup"><span data-stu-id="2567a-116">Gets a symbol reader method, given a method token.</span></span>|  
|[<span data-ttu-id="2567a-117">Método GetMethodByVersion</span><span class="sxs-lookup"><span data-stu-id="2567a-117">GetMethodByVersion Method</span></span>](isymunmanagedreader-getmethodbyversion-method.md)|<span data-ttu-id="2567a-118">Obtém um método de leitor de símbolo, dado um token de método e um número de versão de edição e cópia.</span><span class="sxs-lookup"><span data-stu-id="2567a-118">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span>|  
|[<span data-ttu-id="2567a-119">Método GetMethodFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="2567a-119">GetMethodFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodfromdocumentposition-method.md)|<span data-ttu-id="2567a-120">Retorna o método que contém o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="2567a-120">Returns the method that contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="2567a-121">Método GetMethodsFromDocumentPosition</span><span class="sxs-lookup"><span data-stu-id="2567a-121">GetMethodsFromDocumentPosition Method</span></span>](isymunmanagedreader-getmethodsfromdocumentposition-method.md)|<span data-ttu-id="2567a-122">Retorna uma matriz de métodos, cada um contendo o ponto de interrupção na posição especificada em um documento.</span><span class="sxs-lookup"><span data-stu-id="2567a-122">Returns an array of methods, each of which contains the breakpoint at the given position in a document.</span></span>|  
|[<span data-ttu-id="2567a-123">Método GetMethodVersion</span><span class="sxs-lookup"><span data-stu-id="2567a-123">GetMethodVersion Method</span></span>](isymunmanagedreader-getmethodversion-method.md)|<span data-ttu-id="2567a-124">Obtém a versão do método.</span><span class="sxs-lookup"><span data-stu-id="2567a-124">Gets the method version.</span></span>|  
|[<span data-ttu-id="2567a-125">Método GetNamespaces</span><span class="sxs-lookup"><span data-stu-id="2567a-125">GetNamespaces Method</span></span>](isymunmanagedreader-getnamespaces-method.md)|<span data-ttu-id="2567a-126">Obtém os namespaces definidos no escopo global dentro deste armazenamento de símbolos.</span><span class="sxs-lookup"><span data-stu-id="2567a-126">Gets the namespaces defined at global scope within this symbol store.</span></span>|  
|[<span data-ttu-id="2567a-127">Método GetSymAttribute</span><span class="sxs-lookup"><span data-stu-id="2567a-127">GetSymAttribute Method</span></span>](isymunmanagedreader-getsymattribute-method.md)|<span data-ttu-id="2567a-128">Obtém um atributo personalizado com base no seu nome.</span><span class="sxs-lookup"><span data-stu-id="2567a-128">Gets a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="2567a-129">Método GetSymbolStoreFileName</span><span class="sxs-lookup"><span data-stu-id="2567a-129">GetSymbolStoreFileName Method</span></span>](isymunmanagedreader-getsymbolstorefilename-method.md)|<span data-ttu-id="2567a-130">Fornece o nome de arquivo em disco do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="2567a-130">Provides the on-disk file name of the symbol store.</span></span>|  
|[<span data-ttu-id="2567a-131">Método GetUserEntryPoint</span><span class="sxs-lookup"><span data-stu-id="2567a-131">GetUserEntryPoint Method</span></span>](isymunmanagedreader-getuserentrypoint-method.md)|<span data-ttu-id="2567a-132">Retorna o método que foi especificado como o ponto de entrada do usuário para o módulo, se houver.</span><span class="sxs-lookup"><span data-stu-id="2567a-132">Returns the method that was specified as the user entry point for the module, if any.</span></span>|  
|[<span data-ttu-id="2567a-133">Método GetVariables</span><span class="sxs-lookup"><span data-stu-id="2567a-133">GetVariables Method</span></span>](isymunmanagedreader-getvariables-method.md)|<span data-ttu-id="2567a-134">Retornar uma variável não local, dado seu pai e nome.</span><span class="sxs-lookup"><span data-stu-id="2567a-134">Return a non-local variable, given its parent and name.</span></span>|  
|[<span data-ttu-id="2567a-135">Método Initialize</span><span class="sxs-lookup"><span data-stu-id="2567a-135">Initialize Method</span></span>](isymunmanagedreader-initialize-method.md)|<span data-ttu-id="2567a-136">Inicializa o leitor de símbolos com a interface de importador de metadados à qual esse leitor será associado, juntamente com o nome de arquivo do módulo.</span><span class="sxs-lookup"><span data-stu-id="2567a-136">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>|  
|[<span data-ttu-id="2567a-137">Método ReplaceSymbolStore</span><span class="sxs-lookup"><span data-stu-id="2567a-137">ReplaceSymbolStore Method</span></span>](isymunmanagedreader-replacesymbolstore-method.md)|<span data-ttu-id="2567a-138">Substitui o repositório de símbolos existente por um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="2567a-138">Replaces the existing symbol store with a delta symbol store.</span></span>|  
|[<span data-ttu-id="2567a-139">Método UpdateSymbolStore</span><span class="sxs-lookup"><span data-stu-id="2567a-139">UpdateSymbolStore Method</span></span>](isymunmanagedreader-updatesymbolstore-method.md)|<span data-ttu-id="2567a-140">Atualiza o repositório de símbolos existente com um repositório de símbolos delta.</span><span class="sxs-lookup"><span data-stu-id="2567a-140">Updates the existing symbol store with a delta symbol store.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2567a-141">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2567a-141">Requirements</span></span>  
 <span data-ttu-id="2567a-142">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2567a-142">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2567a-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="2567a-143">See also</span></span>

- [<span data-ttu-id="2567a-144">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="2567a-144">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="2567a-145">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="2567a-145">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
