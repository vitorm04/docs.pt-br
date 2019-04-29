---
title: Interfaces de armazenamento de símbolo de diagnóstico
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787888"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="e2870-102">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="e2870-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="e2870-103">Este tópico descreve as interfaces não gerenciadas que permitem que um compilador gerar informações de símbolo para uso por um depurador.</span><span class="sxs-lookup"><span data-stu-id="e2870-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e2870-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e2870-104">In This Section</span></span>  
 [<span data-ttu-id="e2870-105">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="e2870-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="e2870-106">Fornece métodos que exibem as informações de associação atuais sobre o aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="e2870-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="e2870-107">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="e2870-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="e2870-108">Define a interface para anexar um depurador de servidor chamado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e2870-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="e2870-109">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="e2870-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="e2870-110">Declara os métodos para registrar e cancelar o registro de uma fonte de notificação de conexão.</span><span class="sxs-lookup"><span data-stu-id="e2870-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="e2870-111">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="e2870-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="e2870-112">Declara os métodos de notificação do coletor.</span><span class="sxs-lookup"><span data-stu-id="e2870-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="e2870-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="e2870-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="e2870-114">Declara um método para definir filtros de notificação.</span><span class="sxs-lookup"><span data-stu-id="e2870-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="e2870-115">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="e2870-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="e2870-116">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="e2870-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="e2870-117">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="e2870-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="e2870-118">Essa interface é o complemento de leitura para [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e2870-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="e2870-119">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="e2870-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="e2870-120">Permite a definição de informações do método assíncrono opcional por um símbolo de método.</span><span class="sxs-lookup"><span data-stu-id="e2870-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="e2870-121">Deve ser usado com um método de aberto (ou seja, entre as chamadas para o [método OpenMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)e o [método CloseMethod](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="e2870-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="e2870-122">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="e2870-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="e2870-123">Representa um associador de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e2870-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="e2870-124">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="e2870-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="e2870-125">Representa um associador de símbolo para código não gerenciado e amplia o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="e2870-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="e2870-126">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="e2870-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="e2870-127">Representa um associador de símbolo para código não gerenciado e amplia o `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="e2870-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="e2870-128">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="e2870-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="e2870-129">Fornece acesso às constantes não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e2870-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="e2870-130">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="e2870-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="e2870-131">Descarta os recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="e2870-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="e2870-132">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="e2870-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="e2870-133">Representa um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e2870-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="e2870-134">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="e2870-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="e2870-135">Fornece métodos para gravar em um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e2870-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="e2870-136">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="e2870-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="e2870-137">Fornece métodos para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="e2870-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="e2870-138">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="e2870-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="e2870-139">Representa um método no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e2870-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="e2870-140">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="e2870-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="e2870-141">Representa um namespace.</span><span class="sxs-lookup"><span data-stu-id="e2870-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="e2870-142">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="e2870-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="e2870-143">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis dentro de um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="e2870-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="e2870-144">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="e2870-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="e2870-145">Obtém um método de leitor de símbolo dado um token de método e um número de versão de editar e copiar.</span><span class="sxs-lookup"><span data-stu-id="e2870-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="e2870-146">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="e2870-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="e2870-147">Fornece métodos que obtêm informações de pesquisa do símbolo.</span><span class="sxs-lookup"><span data-stu-id="e2870-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="e2870-148">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="e2870-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="e2870-149">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="e2870-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="e2870-150">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="e2870-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="e2870-151">Representa um escopo léxico dentro de um método e estende o `ISymUnmanagedScope` interface com métodos que obtêm informações sobre constantes definidas dentro do escopo...</span><span class="sxs-lookup"><span data-stu-id="e2870-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="e2870-152">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="e2870-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="e2870-153">Fornece dados de servidor de origem para um módulo.</span><span class="sxs-lookup"><span data-stu-id="e2870-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="e2870-154">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="e2870-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="e2870-155">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="e2870-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="e2870-156">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="e2870-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="e2870-157">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="e2870-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="e2870-158">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="e2870-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="e2870-159">Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="e2870-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="e2870-160">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="e2870-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="e2870-161">Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="e2870-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="e2870-162">Estende o `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="e2870-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="e2870-163">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="e2870-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="e2870-164">Representa um gravador de símbolo e fornece métodos para definir pontos de sequência, documentos, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="e2870-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="e2870-165">Estende o `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="e2870-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="e2870-166">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="e2870-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="e2870-167">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="e2870-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="e2870-168">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="e2870-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="e2870-169">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="e2870-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e2870-170">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="e2870-170">Related Sections</span></span>  
 [<span data-ttu-id="e2870-171">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="e2870-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="e2870-172">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="e2870-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="e2870-173">Depuração</span><span class="sxs-lookup"><span data-stu-id="e2870-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
