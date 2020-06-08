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
ms.openlocfilehash: 34eee8c05e1c356d4c431245c6837bd2b3a89b32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504466"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="ad816-102">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ad816-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="ad816-103">Este tópico descreve as interfaces não gerenciadas que permitem que um compilador gere informações de símbolo para uso por um depurador.</span><span class="sxs-lookup"><span data-stu-id="ad816-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ad816-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ad816-104">In This Section</span></span>  
 [<span data-ttu-id="ad816-105">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="ad816-105">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)  
 <span data-ttu-id="ad816-106">Fornece métodos que exibem informações de associação atuais sobre o aplicativo em execução.</span><span class="sxs-lookup"><span data-stu-id="ad816-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="ad816-107">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="ad816-107">IDebugAutoAttach Interface</span></span>](idebugautoattach-interface.md)  
 <span data-ttu-id="ad816-108">Define a interface para uma anexação automática do depurador invocado pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="ad816-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="ad816-109">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="ad816-109">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)  
 <span data-ttu-id="ad816-110">Declara métodos para registrar e cancelar o registro de uma fonte de notificação de conexão.</span><span class="sxs-lookup"><span data-stu-id="ad816-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="ad816-111">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="ad816-111">INotifySink2 Interface</span></span>](inotifysink2-interface.md)  
 <span data-ttu-id="ad816-112">Declara métodos para notificação de coletor.</span><span class="sxs-lookup"><span data-stu-id="ad816-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="ad816-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="ad816-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)  
 <span data-ttu-id="ad816-114">Declara um método para definir filtros de notificação.</span><span class="sxs-lookup"><span data-stu-id="ad816-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="ad816-115">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="ad816-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="ad816-116">Fornece informações para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="ad816-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="ad816-117">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="ad816-117">ISymUnmanagedAsyncMethod Interface</span></span>](isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="ad816-118">Essa interface é o complemento de leitura para a [interface ISymUnmanagedAsyncMethodPropertiesWriter](isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ad816-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="ad816-119">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="ad816-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="ad816-120">Permite a definição de informações opcionais de método Async por símbolo de método.</span><span class="sxs-lookup"><span data-stu-id="ad816-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="ad816-121">Deve ser usado com um método aberto (ou seja, entre chamadas para o [método OpenMethod](isymunmanagedwriter-openmethod-method.md)e o [método CloseMethod](isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="ad816-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="ad816-122">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="ad816-122">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)  
 <span data-ttu-id="ad816-123">Representa um fichário de símbolo para código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="ad816-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="ad816-124">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="ad816-124">ISymUnmanagedBinder2 Interface</span></span>](isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="ad816-125">Representa um fichário de símbolo para código não gerenciado e estende a `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="ad816-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="ad816-126">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="ad816-126">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="ad816-127">Representa um fichário de símbolo para código não gerenciado e estende a `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="ad816-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="ad816-128">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="ad816-128">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)  
 <span data-ttu-id="ad816-129">Fornece acesso a constantes não gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="ad816-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="ad816-130">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="ad816-130">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)  
 <span data-ttu-id="ad816-131">Descartes de recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="ad816-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="ad816-132">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="ad816-132">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)  
 <span data-ttu-id="ad816-133">Representa um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="ad816-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="ad816-134">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="ad816-134">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="ad816-135">Fornece métodos para gravar em um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="ad816-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="ad816-136">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="ad816-136">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="ad816-137">Fornece métodos para o recurso Editar e continuar.</span><span class="sxs-lookup"><span data-stu-id="ad816-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="ad816-138">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="ad816-138">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)  
 <span data-ttu-id="ad816-139">Representa um método dentro do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="ad816-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="ad816-140">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="ad816-140">ISymUnmanagedNamespace Interface</span></span>](isymunmanagednamespace-interface.md)  
 <span data-ttu-id="ad816-141">Representa um namespace.</span><span class="sxs-lookup"><span data-stu-id="ad816-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="ad816-142">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="ad816-142">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)  
 <span data-ttu-id="ad816-143">Representa um leitor de símbolo que fornece acesso a documentos, métodos e variáveis em um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="ad816-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="ad816-144">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="ad816-144">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)  
 <span data-ttu-id="ad816-145">Obtém um método de leitor de símbolos dado um token de método e um número de versão de edição e cópia.</span><span class="sxs-lookup"><span data-stu-id="ad816-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="ad816-146">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="ad816-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="ad816-147">Fornece métodos que recebem informações de pesquisa de símbolo.</span><span class="sxs-lookup"><span data-stu-id="ad816-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="ad816-148">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="ad816-148">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)  
 <span data-ttu-id="ad816-149">Representa um escopo léxico dentro de um método.</span><span class="sxs-lookup"><span data-stu-id="ad816-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="ad816-150">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="ad816-150">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)  
 <span data-ttu-id="ad816-151">Representa um escopo léxico dentro de um método e estende a `ISymUnmanagedScope` interface com métodos que obtêm informações sobre constantes definidas no escopo.</span><span class="sxs-lookup"><span data-stu-id="ad816-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="ad816-152">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="ad816-152">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="ad816-153">Fornece dados do servidor de origem para um módulo.</span><span class="sxs-lookup"><span data-stu-id="ad816-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="ad816-154">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="ad816-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="ad816-155">Fornece métodos que obtêm informações sobre o caminho de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="ad816-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="ad816-156">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="ad816-156">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)  
 <span data-ttu-id="ad816-157">Representa uma variável, como um parâmetro, uma variável local ou um campo.</span><span class="sxs-lookup"><span data-stu-id="ad816-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="ad816-158">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="ad816-158">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)  
 <span data-ttu-id="ad816-159">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="ad816-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="ad816-160">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="ad816-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="ad816-161">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="ad816-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ad816-162">Estende a `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="ad816-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="ad816-163">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="ad816-163">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="ad816-164">Representa um gravador de símbolo e fornece métodos para definir documentos, pontos de sequência, escopos léxicos e variáveis.</span><span class="sxs-lookup"><span data-stu-id="ad816-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="ad816-165">Estende a `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="ad816-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="ad816-166">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="ad816-166">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="ad816-167">Interface ISymUnmanagedWriter4.</span><span class="sxs-lookup"><span data-stu-id="ad816-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="ad816-168">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="ad816-168">ISymUnmanagedWriter5 Interface</span></span>](isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="ad816-169">Interface ISymUnmanagedWriter5.</span><span class="sxs-lookup"><span data-stu-id="ad816-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ad816-170">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ad816-170">Related Sections</span></span>  
 [<span data-ttu-id="ad816-171">Enumerações de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ad816-171">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="ad816-172">Estruturas de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ad816-172">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="ad816-173">Depuração</span><span class="sxs-lookup"><span data-stu-id="ad816-173">Debugging</span></span>](../debugging/index.md)
