---
title: APIs sem suporte no .NET Core
description: Saiba quais APIs do .NET Framework que sempre lançam uma exceção no .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: f27aeca31226a95dacf100813762eedb56876fbd
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936981"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="d9b9c-103">APIs que sempre lançam exceções no .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9b9c-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="d9b9c-104">As APIs a seguir sempre lançarão um <xref:System.PlatformNotSupportedException> no .NET Core em todos ou em um subconjunto de plataformas.</span><span class="sxs-lookup"><span data-stu-id="d9b9c-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="d9b9c-105">Este artigo organiza os membros de API afetados por namespace.</span><span class="sxs-lookup"><span data-stu-id="d9b9c-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="d9b9c-106">Este artigo é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="d9b9c-106">This article is a work-in-progress.</span></span> <span data-ttu-id="d9b9c-107">Não é uma lista completa de APIs que lançam exceções no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9b9c-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="d9b9c-108">Este artigo não inclui as implementações de interface explícitas para serialização binária que lançam no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d9b9c-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="d9b9c-109">Para obter mais informações, consulte [serialização binária no .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="d9b9c-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="d9b9c-110">System</span><span class="sxs-lookup"><span data-stu-id="d9b9c-110">System</span></span>

| <span data-ttu-id="d9b9c-111">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-111">Member</span></span> | <span data-ttu-id="d9b9c-112">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-113">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-114">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-115">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-116">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-117">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-118">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-119">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-120">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-121">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-122">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="d9b9c-123">{1&gt;{2&gt;System.CodeDom.Compiler&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="d9b9c-124">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-124">Member</span></span> | <span data-ttu-id="d9b9c-125">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-126">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-127">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-128">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="d9b9c-129">{1&gt;System.Collections.Specialized&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="d9b9c-130">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-130">Member</span></span> | <span data-ttu-id="d9b9c-131">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-132">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-133">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-134">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="d9b9c-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="d9b9c-135">System.Configuration</span></span>

| <span data-ttu-id="d9b9c-136">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-136">Member</span></span> | <span data-ttu-id="d9b9c-137">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="d9b9c-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="d9b9c-139">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="d9b9c-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="d9b9c-140">System.Console</span></span>

| <span data-ttu-id="d9b9c-141">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-141">Member</span></span> | <span data-ttu-id="d9b9c-142">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-143">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-143">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-145">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-145">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-147">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-147">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-149">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-149">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="d9b9c-151">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-152">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-153">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-154">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-154">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-155"><xref:System.Console.Title?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="d9b9c-156">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-156">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-158">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-158">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-160">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-160">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-162">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-162">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-164">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="d9b9c-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="d9b9c-165">System.Data.Common</span></span>

| <span data-ttu-id="d9b9c-166">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-166">Member</span></span> | <span data-ttu-id="d9b9c-167">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="d9b9c-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (gera <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="d9b9c-169">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="d9b9c-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="d9b9c-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="d9b9c-171">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-171">Member</span></span> | <span data-ttu-id="d9b9c-172">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="d9b9c-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-174">Linux</span><span class="sxs-lookup"><span data-stu-id="d9b9c-174">Linux</span></span> |
| <span data-ttu-id="d9b9c-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-176">Linux</span><span class="sxs-lookup"><span data-stu-id="d9b9c-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-177">macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-178">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-179">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-180">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-181">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-182">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-183">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-183">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-185">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-185">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="d9b9c-187">macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-187">macOS</span></span> |
| <span data-ttu-id="d9b9c-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-189">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="d9b9c-190">{1&gt;System.IO&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-190">System.IO</span></span>

| <span data-ttu-id="d9b9c-191">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-191">Member</span></span> | <span data-ttu-id="d9b9c-192">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-193">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-194">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="d9b9c-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="d9b9c-195">System.IO.Pipes</span></span>

| <span data-ttu-id="d9b9c-196">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-196">Member</span></span> | <span data-ttu-id="d9b9c-197">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-198">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-199">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-200">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-201">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-201">Linux and macOS</span></span> |
| <span data-ttu-id="d9b9c-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-203">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-204">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="d9b9c-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="d9b9c-205">System.Media</span></span>

| <span data-ttu-id="d9b9c-206">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-206">Member</span></span> | <span data-ttu-id="d9b9c-207">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-208">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="d9b9c-209">{1&gt;{2&gt;System.Net&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-209">System.Net</span></span>

| <span data-ttu-id="d9b9c-210">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-210">Member</span></span> | <span data-ttu-id="d9b9c-211">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-212">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-213">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-214">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-215">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-216">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-217">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-218">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-219">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-220">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-221">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-222">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-223">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-224">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-225">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-226">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-227">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-228">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="d9b9c-229">{1&gt;System.Net.NetworkInformation&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="d9b9c-230">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-230">Member</span></span> | <span data-ttu-id="d9b9c-231">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="d9b9c-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="d9b9c-233">System.Net.Sockets</span></span>

| <span data-ttu-id="d9b9c-234">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-234">Member</span></span> | <span data-ttu-id="d9b9c-235">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-236">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="d9b9c-237">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="d9b9c-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="d9b9c-238">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-238">Member</span></span> | <span data-ttu-id="d9b9c-239">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-239">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-240">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="d9b9c-241">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="d9b9c-241">System.Reflection</span></span>

| <span data-ttu-id="d9b9c-242">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-242">Member</span></span> | <span data-ttu-id="d9b9c-243">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-243">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-244">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-245">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-246">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-247">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-248">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-249">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-250">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="d9b9c-251">{1&gt;{2&gt;System.Runtime.CompilerServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="d9b9c-252">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-252">Member</span></span> | <span data-ttu-id="d9b9c-253">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-253">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-254">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="d9b9c-255">{1&gt;{2&gt;System.Runtime.InteropServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="d9b9c-256">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-256">Member</span></span> | <span data-ttu-id="d9b9c-257">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-257">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-258">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-259">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-260">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-261">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-262">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-263">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-264">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="d9b9c-265">{1&gt;System.Runtime.Serialization&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="d9b9c-266">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-266">Member</span></span> | <span data-ttu-id="d9b9c-267">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-267">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-268">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="d9b9c-269">{1&gt;{2&gt;System.Security&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-269">System.Security</span></span>

| <span data-ttu-id="d9b9c-270">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-270">Member</span></span> | <span data-ttu-id="d9b9c-271">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-271">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-272">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-273">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-274">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-275">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-276">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-277">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-278">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-279">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-280">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-281">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-282">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-283">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-284">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-285">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="d9b9c-286">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="d9b9c-286">System.Security.Claims</span></span>

| <span data-ttu-id="d9b9c-287">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-287">Member</span></span> | <span data-ttu-id="d9b9c-288">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-288">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-289">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-290">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-291">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-292">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-293">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="d9b9c-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="d9b9c-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="d9b9c-295">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-295">Member</span></span> | <span data-ttu-id="d9b9c-296">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-296">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-297">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-298">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-299">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-300">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-301">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-302">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-303">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-304">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-305">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-306">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-307">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-308">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-309">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-310">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-311">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-312">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-313">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-314">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-315">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-316">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-317">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-318">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-319">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-320">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-321">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="d9b9c-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-322">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-323">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-324">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-325">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="d9b9c-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="d9b9c-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="d9b9c-327">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-327">Member</span></span> | <span data-ttu-id="d9b9c-328">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-329">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-330">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-331">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="d9b9c-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="d9b9c-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="d9b9c-333">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-333">Member</span></span> | <span data-ttu-id="d9b9c-334">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-335">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-336">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-337">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-337">All</span></span> |
| <span data-ttu-id="d9b9c-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="d9b9c-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="d9b9c-339">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="d9b9c-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="d9b9c-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="d9b9c-341">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-341">Member</span></span> | <span data-ttu-id="d9b9c-342">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-343">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="d9b9c-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="d9b9c-344">System.Security.Policy</span></span>

| <span data-ttu-id="d9b9c-345">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-345">Member</span></span> | <span data-ttu-id="d9b9c-346">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-347">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="d9b9c-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="d9b9c-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="d9b9c-349">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-349">Member</span></span> | <span data-ttu-id="d9b9c-350">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-351">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="d9b9c-352">{1&gt;System.Text.RegularExpressions&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="d9b9c-353">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-353">Member</span></span> | <span data-ttu-id="d9b9c-354">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-355">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="d9b9c-356">{1&gt;System.Threading&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-356">System.Threading</span></span>

| <span data-ttu-id="d9b9c-357">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-357">Member</span></span> | <span data-ttu-id="d9b9c-358">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-359">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-360">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-361">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-362">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-363">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-364">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="d9b9c-365">{1&gt;System.Xml&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-365">System.Xml</span></span>

| <span data-ttu-id="d9b9c-366">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-366">Member</span></span> | <span data-ttu-id="d9b9c-367">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="d9b9c-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-368">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-369">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="d9b9c-370">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="d9b9c-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="d9b9c-371">Veja também</span><span class="sxs-lookup"><span data-stu-id="d9b9c-371">See also</span></span>

- [<span data-ttu-id="d9b9c-372">Alterações recentes de migração do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9b9c-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="d9b9c-373">Serialização binária no .NET Core</span><span class="sxs-lookup"><span data-stu-id="d9b9c-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="d9b9c-374">Analisador de portabilidade .NET</span><span class="sxs-lookup"><span data-stu-id="d9b9c-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
