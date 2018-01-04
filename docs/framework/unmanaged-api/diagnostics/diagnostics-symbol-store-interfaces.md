---
title: "Interfaces de armazenamento de símbolo de diagnóstico"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9a9550bf1e3e5500356584b1bdd53f5d3061e190
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="b9a6f-102">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b9a6f-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="b9a6f-103">Este tópico descreve as interfaces não gerenciadas que permitem que um compilador para gerar informações de símbolo para uso por um depurador.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b9a6f-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="b9a6f-104">In This Section</span></span>  
 [<span data-ttu-id="b9a6f-105">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="b9a6f-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="b9a6f-106">Fornece métodos que exibem as informações de associação atuais sobre o aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="b9a6f-107">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="b9a6f-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="b9a6f-108">Define a interface para anexar um depurador de servidor chamado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="b9a6f-109">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="b9a6f-110">Declara os métodos para registrar e cancelar o registro de uma fonte de conexão de notificação.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="b9a6f-111">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="b9a6f-112">Declara os métodos de notificação de coletor.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="b9a6f-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="b9a6f-114">Declara um método para definir filtros de notificação.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="b9a6f-115">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="b9a6f-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="b9a6f-116">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="b9a6f-117">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="b9a6f-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="b9a6f-118">Essa interface é o complemento de leitura para [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b9a6f-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="b9a6f-119">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="b9a6f-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="b9a6f-120">Permite a definição das informações de método assíncrono opcional por símbolo do método.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="b9a6f-121">Deve usar um método aberto (ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)e [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="b9a6f-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="b9a6f-122">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="b9a6f-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="b9a6f-123">Representa um associador de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="b9a6f-124">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="b9a6f-125">Representa um associador de símbolo para código não gerenciado e estende o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="b9a6f-126">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="b9a6f-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="b9a6f-127">Representa um associador de símbolo para código não gerenciado e estende o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="b9a6f-128">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="b9a6f-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="b9a6f-129">Fornece acesso às constantes não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="b9a6f-130">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="b9a6f-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="b9a6f-131">Libera recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="b9a6f-132">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="b9a6f-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="b9a6f-133">Representa um documento referenciado por um repositório de símbolo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="b9a6f-134">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="b9a6f-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="b9a6f-135">Fornece métodos para gravar em um documento referenciado por um repositório de símbolo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="b9a6f-136">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="b9a6f-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="b9a6f-137">Fornece métodos para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="b9a6f-138">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="b9a6f-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="b9a6f-139">Representa um método no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="b9a6f-140">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="b9a6f-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="b9a6f-141">Representa um namespace.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="b9a6f-142">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="b9a6f-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="b9a6f-143">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um armazenamento de símbolo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="b9a6f-144">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="b9a6f-145">Obtém um método de leitor de símbolo dado um token de método e um número de versão de editar e copiar.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="b9a6f-146">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="b9a6f-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="b9a6f-147">Fornece métodos que obtêm informações de pesquisa do símbolo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="b9a6f-148">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="b9a6f-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="b9a6f-149">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="b9a6f-150">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="b9a6f-151">Representa um escopo léxico dentro de um método e estende o `ISymUnmanagedScope` interface com métodos que obtêm informações sobre constantes definidas dentro do escopo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="b9a6f-152">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="b9a6f-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="b9a6f-153">Fornece dados de servidor de origem para um módulo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="b9a6f-154">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="b9a6f-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="b9a6f-155">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="b9a6f-156">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="b9a6f-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="b9a6f-157">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="b9a6f-158">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="b9a6f-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="b9a6f-159">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="b9a6f-160">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="b9a6f-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="b9a6f-161">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b9a6f-162">Estende o `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="b9a6f-163">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="b9a6f-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="b9a6f-164">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos de léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="b9a6f-165">Estende o `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="b9a6f-166">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="b9a6f-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="b9a6f-167">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="b9a6f-168">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="b9a6f-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="b9a6f-169">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b9a6f-170">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="b9a6f-170">Related Sections</span></span>  
 [<span data-ttu-id="b9a6f-171">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b9a6f-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="b9a6f-172">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="b9a6f-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="b9a6f-173">Depuração</span><span class="sxs-lookup"><span data-stu-id="b9a6f-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
