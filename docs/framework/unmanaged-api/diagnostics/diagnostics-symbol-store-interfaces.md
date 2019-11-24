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
ms.openlocfilehash: bdb691570a9a2bf7bd2bb21af500b06c10b0bc53
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448530"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="4064e-102">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4064e-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="4064e-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span><span class="sxs-lookup"><span data-stu-id="4064e-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4064e-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4064e-104">In This Section</span></span>  
 [<span data-ttu-id="4064e-105">Interface IBindingDisplay</span><span class="sxs-lookup"><span data-stu-id="4064e-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="4064e-106">Provides methods that display current binding information about the running application.</span><span class="sxs-lookup"><span data-stu-id="4064e-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="4064e-107">Interface IDebugAutoAttach</span><span class="sxs-lookup"><span data-stu-id="4064e-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="4064e-108">Defines the interface for a server-invoked debugger auto attach.</span><span class="sxs-lookup"><span data-stu-id="4064e-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="4064e-109">Interface INotifyConnection2</span><span class="sxs-lookup"><span data-stu-id="4064e-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="4064e-110">Declares methods for registering and unregistering a connection notification source.</span><span class="sxs-lookup"><span data-stu-id="4064e-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="4064e-111">Interface INotifySink2</span><span class="sxs-lookup"><span data-stu-id="4064e-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="4064e-112">Declares methods for sink notification.</span><span class="sxs-lookup"><span data-stu-id="4064e-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="4064e-113">Interface INotifySource2</span><span class="sxs-lookup"><span data-stu-id="4064e-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="4064e-114">Declares a method for setting notification filters.</span><span class="sxs-lookup"><span data-stu-id="4064e-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="4064e-115">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="4064e-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="4064e-116">Provides information for the Edit and Continue feature.</span><span class="sxs-lookup"><span data-stu-id="4064e-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="4064e-117">Interface ISymUnmanagedAsyncMethod</span><span class="sxs-lookup"><span data-stu-id="4064e-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="4064e-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4064e-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="4064e-119">Interface ISymUnmanagedAsyncMethodPropertiesWriter</span><span class="sxs-lookup"><span data-stu-id="4064e-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="4064e-120">Allows definition of optional async method information per method symbol.</span><span class="sxs-lookup"><span data-stu-id="4064e-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="4064e-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span><span class="sxs-lookup"><span data-stu-id="4064e-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="4064e-122">Interface ISymUnmanagedBinder</span><span class="sxs-lookup"><span data-stu-id="4064e-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="4064e-123">Represents a symbol binder for unmanaged code.</span><span class="sxs-lookup"><span data-stu-id="4064e-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="4064e-124">Interface ISymUnmanagedBinder2</span><span class="sxs-lookup"><span data-stu-id="4064e-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="4064e-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="4064e-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="4064e-126">Interface ISymUnmanagedBinder3</span><span class="sxs-lookup"><span data-stu-id="4064e-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="4064e-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span><span class="sxs-lookup"><span data-stu-id="4064e-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="4064e-128">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="4064e-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="4064e-129">Provides access to unmanaged constants.</span><span class="sxs-lookup"><span data-stu-id="4064e-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="4064e-130">Interface ISymUnmanagedDispose</span><span class="sxs-lookup"><span data-stu-id="4064e-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="4064e-131">Disposes of unmanaged resources.</span><span class="sxs-lookup"><span data-stu-id="4064e-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="4064e-132">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="4064e-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="4064e-133">Representa um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="4064e-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="4064e-134">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="4064e-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="4064e-135">Fornece métodos para gravar em um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="4064e-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="4064e-136">Interface ISymUnmanagedENCUpdate</span><span class="sxs-lookup"><span data-stu-id="4064e-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="4064e-137">Provides methods for the Edit and Continue feature.</span><span class="sxs-lookup"><span data-stu-id="4064e-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="4064e-138">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="4064e-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="4064e-139">Represents a method within the symbol store.</span><span class="sxs-lookup"><span data-stu-id="4064e-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="4064e-140">Interface ISymUnmanagedNamespace</span><span class="sxs-lookup"><span data-stu-id="4064e-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="4064e-141">Representa um namespace.</span><span class="sxs-lookup"><span data-stu-id="4064e-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="4064e-142">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="4064e-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="4064e-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span><span class="sxs-lookup"><span data-stu-id="4064e-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="4064e-144">Interface ISymUnmanagedReader2</span><span class="sxs-lookup"><span data-stu-id="4064e-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="4064e-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span><span class="sxs-lookup"><span data-stu-id="4064e-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="4064e-146">Interface ISymUnmanagedReaderSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="4064e-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="4064e-147">Provides methods that get symbol search information.</span><span class="sxs-lookup"><span data-stu-id="4064e-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="4064e-148">Interface ISymUnmanagedScope</span><span class="sxs-lookup"><span data-stu-id="4064e-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="4064e-149">Represents a lexical scope within a method.</span><span class="sxs-lookup"><span data-stu-id="4064e-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="4064e-150">Interface ISymUnmanagedScope2</span><span class="sxs-lookup"><span data-stu-id="4064e-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="4064e-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span><span class="sxs-lookup"><span data-stu-id="4064e-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="4064e-152">Interface ISymUnmanagedSourceServerModule</span><span class="sxs-lookup"><span data-stu-id="4064e-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="4064e-153">Provides source server data for a module.</span><span class="sxs-lookup"><span data-stu-id="4064e-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="4064e-154">Interface ISymUnmanagedSymbolSearchInfo</span><span class="sxs-lookup"><span data-stu-id="4064e-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="4064e-155">Provides methods that get information about the search path.</span><span class="sxs-lookup"><span data-stu-id="4064e-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="4064e-156">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="4064e-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="4064e-157">Represents a variable, such as a parameter, a local variable, or a field.</span><span class="sxs-lookup"><span data-stu-id="4064e-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="4064e-158">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="4064e-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="4064e-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span><span class="sxs-lookup"><span data-stu-id="4064e-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="4064e-160">Interface ISymUnmanagedWriter2</span><span class="sxs-lookup"><span data-stu-id="4064e-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="4064e-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span><span class="sxs-lookup"><span data-stu-id="4064e-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="4064e-162">Extends the `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="4064e-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="4064e-163">Interface ISymUnmanagedWriter3</span><span class="sxs-lookup"><span data-stu-id="4064e-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="4064e-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span><span class="sxs-lookup"><span data-stu-id="4064e-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="4064e-165">Extends the `ISymUnmanagedWriter` interface.</span><span class="sxs-lookup"><span data-stu-id="4064e-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="4064e-166">Interface ISymUnmanagedWriter4</span><span class="sxs-lookup"><span data-stu-id="4064e-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="4064e-167">ISymUnmanagedWriter4 interface.</span><span class="sxs-lookup"><span data-stu-id="4064e-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="4064e-168">Interface ISymUnmanagedWriter5</span><span class="sxs-lookup"><span data-stu-id="4064e-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="4064e-169">ISymUnmanagedWriter5 interface.</span><span class="sxs-lookup"><span data-stu-id="4064e-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4064e-170">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4064e-170">Related Sections</span></span>  
 [<span data-ttu-id="4064e-171">Enumerações do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4064e-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="4064e-172">Estruturas de repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="4064e-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="4064e-173">Depuração</span><span class="sxs-lookup"><span data-stu-id="4064e-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
