---
title: Classe Logging (System.Net)
ms.date: 06/12/2020
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Logging
- System.Net.Logging.Associate
- System.Net.Logging.Enter
- System.Net.Logging.Exception
- System.Net.Logging.Exit
- System.Net.Logging.get_Http
- System.Net.Logging.get_On
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: ad85fdd41252ed147eb5fe1a9db029db046d720c
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990302"
---
# <a name="logging-class"></a><span data-ttu-id="ee87a-102">Classe Logging</span><span class="sxs-lookup"><span data-stu-id="ee87a-102">Logging class</span></span>

<span data-ttu-id="ee87a-103">Fornece a funcionalidade de log de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-103">Provides trace logging functionality.</span></span>

```csharp
internal class Logging
```

> [!WARNING]
> <span data-ttu-id="ee87a-104">Essa classe é interna e não deve ser usada diretamente no seu código.</span><span class="sxs-lookup"><span data-stu-id="ee87a-104">This class is internal and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="ee87a-105">A Microsoft não oferece suporte ao uso dessa classe em um aplicativo de produção em nenhuma circunstância.</span><span class="sxs-lookup"><span data-stu-id="ee87a-105">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="associate-method"></a><span data-ttu-id="ee87a-106">Associar método</span><span class="sxs-lookup"><span data-stu-id="ee87a-106">Associate method</span></span>

<span data-ttu-id="ee87a-107">Registra as informações de que dois objetos estão associados entre si.</span><span class="sxs-lookup"><span data-stu-id="ee87a-107">Logs information that two objects are associated with each other.</span></span>

```csharp
internal static void Associate(TraceSource traceSource, object objA, object objB)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-108">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-108">Parameters</span></span>

- <span data-ttu-id="ee87a-109">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-109">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-110">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-110">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-111">`objA` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-111">`objA` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-112">O objeto ao qual associar `objB` .</span><span class="sxs-lookup"><span data-stu-id="ee87a-112">The object to associate with `objB`.</span></span>

- <span data-ttu-id="ee87a-113">`objB` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-113">`objB` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-114">O objeto ao qual associar `objA` .</span><span class="sxs-lookup"><span data-stu-id="ee87a-114">The object to associate with `objA`.</span></span>

## <a name="entertracesource-object-string-string-method"></a><span data-ttu-id="ee87a-115">Inserir o método (Tracename, Object, String, String)</span><span class="sxs-lookup"><span data-stu-id="ee87a-115">Enter(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="ee87a-116">Registra a entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-116">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-117">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-117">Parameters</span></span>

- <span data-ttu-id="ee87a-118">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-118">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-119">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-119">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-120">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-120">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-121">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-121">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-122">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-122">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-123">O método que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="ee87a-123">The method that is being entered.</span></span>

- <span data-ttu-id="ee87a-124">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-124">`param` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-125">Os parâmetros que foram passados para o método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-125">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-object-string-object-method"></a><span data-ttu-id="ee87a-126">Inserir o método (Tracename, Object, String, Object)</span><span class="sxs-lookup"><span data-stu-id="ee87a-126">Enter(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="ee87a-127">Registra a entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-127">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, object obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-128">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-128">Parameters</span></span>

- <span data-ttu-id="ee87a-129">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-129">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-130">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-130">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-131">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-131">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-132">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-132">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-133">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-133">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-134">O método que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="ee87a-134">The method that is being entered.</span></span>

- <span data-ttu-id="ee87a-135">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-135">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-136">Os parâmetros que foram passados para o método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-136">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-string-method"></a><span data-ttu-id="ee87a-137">Inserir o método (Tracename, String, String, String)</span><span class="sxs-lookup"><span data-stu-id="ee87a-137">Enter(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="ee87a-138">Registra a entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-138">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, string param)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-139">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-139">Parameters</span></span>

- <span data-ttu-id="ee87a-140">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-140">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-141">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-141">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-142">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-142">`obj` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-143">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-143">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-144">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-144">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-145">O método que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="ee87a-145">The method that is being entered.</span></span>

- <span data-ttu-id="ee87a-146">`param` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-146">`param` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-147">Os parâmetros que foram passados para o método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-147">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-object-method"></a><span data-ttu-id="ee87a-148">Inserir o método (Tracename, String, String, Object)</span><span class="sxs-lookup"><span data-stu-id="ee87a-148">Enter(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="ee87a-149">Registra a entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-149">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string obj, string method, object paramObject)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-150">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-150">Parameters</span></span>

- <span data-ttu-id="ee87a-151">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-151">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-152">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-152">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-153">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-153">`obj` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-154">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-154">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-155">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-155">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-156">O método que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="ee87a-156">The method that is being entered.</span></span>

- <span data-ttu-id="ee87a-157">`paramObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-157">`paramObject` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-158">Os parâmetros que foram passados para o método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-158">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-string-method"></a><span data-ttu-id="ee87a-159">Insira o método (Tracename, String, String)</span><span class="sxs-lookup"><span data-stu-id="ee87a-159">Enter(TraceSource, string, string) method</span></span>

<span data-ttu-id="ee87a-160">Registra a entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-160">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-161">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-161">Parameters</span></span>

- <span data-ttu-id="ee87a-162">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-162">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-163">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-163">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-164">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-164">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-165">O método que está sendo inserido.</span><span class="sxs-lookup"><span data-stu-id="ee87a-165">The method that is being entered.</span></span>

- <span data-ttu-id="ee87a-166">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-166">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-167">Os parâmetros que foram passados para o método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-167">The parameters that were passed to the method.</span></span>

## <a name="entertracesource-string-method"></a><span data-ttu-id="ee87a-168">Insira o método (Tracename, String)</span><span class="sxs-lookup"><span data-stu-id="ee87a-168">Enter(TraceSource, string) method</span></span>

<span data-ttu-id="ee87a-169">Registra a entrada em um método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-169">Logs entrance to a method.</span></span>

```csharp
internal static void Enter(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-170">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-170">Parameters</span></span>

- <span data-ttu-id="ee87a-171">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-171">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-172">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-172">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-173">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-173">`msg` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-174">A mensagem de entrada para fazer logon na origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-174">The entrance message to log to the trace source.</span></span>

## <a name="exception-method"></a><span data-ttu-id="ee87a-175">Método Exception</span><span class="sxs-lookup"><span data-stu-id="ee87a-175">Exception method</span></span>

<span data-ttu-id="ee87a-176">Registra uma exceção e restaura o recuo.</span><span class="sxs-lookup"><span data-stu-id="ee87a-176">Logs an exception and restores indentation.</span></span>

```csharp
internal static void Exception(TraceSource traceSource, object obj, string method, Exception e)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-177">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-177">Parameters</span></span>

- <span data-ttu-id="ee87a-178">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-178">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-179">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-179">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-180">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-180">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-181">O objeto no qual o método que gerou uma exceção foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-181">The object that the method that threw an exception was called on.</span></span>

- <span data-ttu-id="ee87a-182">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-182">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-183">O método que gerou a exceção.</span><span class="sxs-lookup"><span data-stu-id="ee87a-183">The method that threw the exception.</span></span>

- <span data-ttu-id="ee87a-184">`e` <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="ee87a-184">`e` <xref:System.Exception></span></span>

  <span data-ttu-id="ee87a-185">A exceção que foi gerada.</span><span class="sxs-lookup"><span data-stu-id="ee87a-185">The exception that was thrown.</span></span>

## <a name="exittracesource-object-string-object-method"></a><span data-ttu-id="ee87a-186">Método Exit (Tracename, Object, String, Object)</span><span class="sxs-lookup"><span data-stu-id="ee87a-186">Exit(TraceSource, object, string, object) method</span></span>

<span data-ttu-id="ee87a-187">Os logs saem de uma função.</span><span class="sxs-lookup"><span data-stu-id="ee87a-187">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-188">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-188">Parameters</span></span>

- <span data-ttu-id="ee87a-189">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-189">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-190">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-190">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-191">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-191">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-192">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-192">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-193">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-193">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-194">O método que está sendo encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-194">The method that is being exited.</span></span>

- <span data-ttu-id="ee87a-195">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-195">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-196">O valor que está sendo retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-196">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-object-method"></a><span data-ttu-id="ee87a-197">Método Exit (Tracename, String, String, Object)</span><span class="sxs-lookup"><span data-stu-id="ee87a-197">Exit(TraceSource, string, string, object) method</span></span>

<span data-ttu-id="ee87a-198">Os logs saem de uma função.</span><span class="sxs-lookup"><span data-stu-id="ee87a-198">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, object retObject)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-199">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-199">Parameters</span></span>

- <span data-ttu-id="ee87a-200">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-200">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-201">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-201">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-202">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-202">`obj` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-203">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-203">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-204">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-204">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-205">O método que está sendo encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-205">The method that is being exited.</span></span>

- <span data-ttu-id="ee87a-206">`retObject` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-206">`retObject` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-207">O valor que está sendo retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-207">The value that's being returned by the method.</span></span>

## <a name="exittracesource-object-string-string-method"></a><span data-ttu-id="ee87a-208">Exit (Tracename, Object, String, String) do método</span><span class="sxs-lookup"><span data-stu-id="ee87a-208">Exit(TraceSource, object, string, string) method</span></span>

<span data-ttu-id="ee87a-209">Os logs saem de uma função.</span><span class="sxs-lookup"><span data-stu-id="ee87a-209">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, object obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-210">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-210">Parameters</span></span>

- <span data-ttu-id="ee87a-211">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-211">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-212">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-212">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-213">`obj` <xref:System.Object></span><span class="sxs-lookup"><span data-stu-id="ee87a-213">`obj` <xref:System.Object></span></span>

  <span data-ttu-id="ee87a-214">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-214">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-215">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-215">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-216">O método que está sendo encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-216">The method that is being exited.</span></span>

- <span data-ttu-id="ee87a-217">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-217">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-218">O valor que está sendo retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-218">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-string-method"></a><span data-ttu-id="ee87a-219">Exit (Tracename, String, String, String) do método</span><span class="sxs-lookup"><span data-stu-id="ee87a-219">Exit(TraceSource, string, string, string) method</span></span>

<span data-ttu-id="ee87a-220">Os logs saem de uma função.</span><span class="sxs-lookup"><span data-stu-id="ee87a-220">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string obj, string method, string retValue)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-221">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-221">Parameters</span></span>

- <span data-ttu-id="ee87a-222">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-222">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-223">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-223">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-224">`obj` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-224">`obj` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-225">O objeto no qual o método foi chamado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-225">The object that the method was called on.</span></span>

- <span data-ttu-id="ee87a-226">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-226">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-227">O método que está sendo encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-227">The method that is being exited.</span></span>

- <span data-ttu-id="ee87a-228">`retValue` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-228">`retValue` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-229">O valor que está sendo retornado pelo método.</span><span class="sxs-lookup"><span data-stu-id="ee87a-229">The value that's being returned by the method.</span></span>

## <a name="exittracesource-string-string-method"></a><span data-ttu-id="ee87a-230">Método Exit (Tracename, String, String)</span><span class="sxs-lookup"><span data-stu-id="ee87a-230">Exit(TraceSource, string, string) method</span></span>

<span data-ttu-id="ee87a-231">Os logs saem de uma função.</span><span class="sxs-lookup"><span data-stu-id="ee87a-231">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string method, string parameters)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-232">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-232">Parameters</span></span>

- <span data-ttu-id="ee87a-233">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-233">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-234">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-234">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-235">`method` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-235">`method` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-236">O método que está sendo encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-236">The method that is being exited.</span></span>

- <span data-ttu-id="ee87a-237">`parameters` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-237">`parameters` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-238">Os parâmetros que foram passados para o método que está sendo encerrado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-238">The parameters that were passed to the method that's being exited.</span></span>

## <a name="exittracesource-string-method"></a><span data-ttu-id="ee87a-239">Método Exit (Tracename, String)</span><span class="sxs-lookup"><span data-stu-id="ee87a-239">Exit(TraceSource, string) method</span></span>

<span data-ttu-id="ee87a-240">Os logs saem de uma função.</span><span class="sxs-lookup"><span data-stu-id="ee87a-240">Logs exit from a function.</span></span>

```csharp
internal static void Exit(TraceSource traceSource, string msg)
```

### <a name="parameters"></a><span data-ttu-id="ee87a-241">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="ee87a-241">Parameters</span></span>

- <span data-ttu-id="ee87a-242">`traceSource` <xref:System.Diagnostics.TraceSource></span><span class="sxs-lookup"><span data-stu-id="ee87a-242">`traceSource` <xref:System.Diagnostics.TraceSource></span></span>

  <span data-ttu-id="ee87a-243">A origem do rastreamento no qual registrar o evento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-243">The trace source to log the event to.</span></span>

- <span data-ttu-id="ee87a-244">`msg` <xref:System.String></span><span class="sxs-lookup"><span data-stu-id="ee87a-244">`msg` <xref:System.String></span></span>

  <span data-ttu-id="ee87a-245">A mensagem de saída a ser registrada na origem do rastreamento.</span><span class="sxs-lookup"><span data-stu-id="ee87a-245">The exit message to log to the trace source.</span></span>

## <a name="http-property"></a><span data-ttu-id="ee87a-246">Propriedade http</span><span class="sxs-lookup"><span data-stu-id="ee87a-246">Http property</span></span>

<span data-ttu-id="ee87a-247">Obtém a origem do rastreamento para "System .net. http".</span><span class="sxs-lookup"><span data-stu-id="ee87a-247">Gets the trace source for "System.Net.Http".</span></span>

```csharp
internal static TraceSource Http { get; }
```

### <a name="property-value"></a><span data-ttu-id="ee87a-248">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="ee87a-248">Property value</span></span>

<xref:System.Diagnostics.TraceSource>\
<span data-ttu-id="ee87a-249">A origem do rastreamento para "System .net. http" ou `null` se o registro em log não estiver habilitado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-249">The trace source for "System.Net.Http", or `null` if logging is not enabled.</span></span>

## <a name="on-property"></a><span data-ttu-id="ee87a-250">Na propriedade</span><span class="sxs-lookup"><span data-stu-id="ee87a-250">On property</span></span>

<span data-ttu-id="ee87a-251">Obtém um valor que indica se o registro em log está habilitado.</span><span class="sxs-lookup"><span data-stu-id="ee87a-251">Gets a value that indicates whether logging is enabled.</span></span>

```csharp
internal static bool On { get; }
```

### <a name="property-value"></a><span data-ttu-id="ee87a-252">Valor da propriedade</span><span class="sxs-lookup"><span data-stu-id="ee87a-252">Property value</span></span>

<xref:System.Boolean>\
<span data-ttu-id="ee87a-253">O valor será `true` se o registro em log estiver habilitado; caso contrário, o valor será `false`.</span><span class="sxs-lookup"><span data-stu-id="ee87a-253">`true` if logging is enabled; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee87a-254">Requisitos</span><span class="sxs-lookup"><span data-stu-id="ee87a-254">Requirements</span></span>

<span data-ttu-id="ee87a-255">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="ee87a-255">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="ee87a-256">**Assembly:** Sistema (em System.dll)</span><span class="sxs-lookup"><span data-stu-id="ee87a-256">**Assembly:** System (in System.dll)</span></span>
