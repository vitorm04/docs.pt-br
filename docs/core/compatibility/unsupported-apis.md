---
title: APIs sem suporte no .NET Core
description: Saiba quais APIs do .NET Framework que sempre lançam uma exceção no .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 0cb533f10d53fd3d287265032e3de13c242a8ae0
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901491"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="fd495-103">APIs que sempre lançam exceções no .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd495-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="fd495-104">As APIs a seguir sempre terão um <xref:System.PlatformNotSupportedException> quando executadas no .NET Core na plataforma especificada.</span><span class="sxs-lookup"><span data-stu-id="fd495-104">The following APIs will always through a <xref:System.PlatformNotSupportedException> when run on .NET Core on the specified platform.</span></span>

<span data-ttu-id="fd495-105">Este artigo organiza os membros de API afetados por namespace.</span><span class="sxs-lookup"><span data-stu-id="fd495-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="fd495-106">Este artigo é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="fd495-106">This article is a work-in-progress.</span></span> <span data-ttu-id="fd495-107">Não é uma lista completa de APIs que lançam exceções no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd495-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="fd495-108">Este artigo não inclui as implementações de interface explícitas para serialização binária que lançam no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd495-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="fd495-109">Para obter mais informações, consulte [serialização binária no .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="fd495-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="fd495-110">System</span><span class="sxs-lookup"><span data-stu-id="fd495-110">System</span></span>

| <span data-ttu-id="fd495-111">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-111">Member</span></span> | <span data-ttu-id="fd495-112">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-112">Platform</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-113">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="fd495-114">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="fd495-115">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="fd495-116">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-117">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="fd495-118">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="fd495-119">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="fd495-120">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-121">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="fd495-122">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="fd495-123">{1&gt;{2&gt;System.CodeDom.Compiler&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="fd495-124">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-124">Member</span></span> | <span data-ttu-id="fd495-125">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-125">Platform</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-126">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-127">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-128">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="fd495-129">{1&gt;System.Collections.Specialized&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="fd495-130">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-130">Member</span></span> | <span data-ttu-id="fd495-131">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-131">Platform</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-132">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-133">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="fd495-134">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="fd495-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="fd495-135">System.Configuration</span></span>

| <span data-ttu-id="fd495-136">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-136">Member</span></span> | <span data-ttu-id="fd495-137">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-137">Platform</span></span> |
| - | - |
| <span data-ttu-id="fd495-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="fd495-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="fd495-139">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="fd495-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="fd495-140">System.Console</span></span>

| <span data-ttu-id="fd495-141">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-141">Member</span></span> | <span data-ttu-id="fd495-142">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-142">Platform</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="fd495-143">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-143">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-145">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-145">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-147">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-147">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-149">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-149">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="fd495-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="fd495-151">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-152">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-153">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-154">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-154">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-155"><xref:System.Console.Title?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="fd495-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="fd495-156">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-156">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-158">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-158">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-160">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-160">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-162">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-162">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-164">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="fd495-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="fd495-165">System.Data.Common</span></span>

| <span data-ttu-id="fd495-166">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-166">Member</span></span> | <span data-ttu-id="fd495-167">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-167">Platform</span></span> |
| - | - |
| <span data-ttu-id="fd495-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (gera <xref:System.NotSupportedException>)</span><span class="sxs-lookup"><span data-stu-id="fd495-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="fd495-169">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="fd495-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="fd495-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="fd495-171">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-171">Member</span></span> | <span data-ttu-id="fd495-172">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-172">Platform</span></span> |
| - | - |
| <span data-ttu-id="fd495-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-174">Linux</span><span class="sxs-lookup"><span data-stu-id="fd495-174">Linux</span></span> |
| <span data-ttu-id="fd495-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-176">Linux</span><span class="sxs-lookup"><span data-stu-id="fd495-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="fd495-177">macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="fd495-178">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-179">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="fd495-180">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="fd495-181">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="fd495-182">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="fd495-183">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-183">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-185">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-185">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="fd495-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="fd495-187">macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-187">macOS</span></span> |
| <span data-ttu-id="fd495-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-189">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="fd495-190">{1&gt;System.IO&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-190">System.IO</span></span>

| <span data-ttu-id="fd495-191">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-191">Member</span></span> | <span data-ttu-id="fd495-192">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-192">Platform</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-193">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-194">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="fd495-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="fd495-195">System.IO.Pipes</span></span>

| <span data-ttu-id="fd495-196">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-196">Member</span></span> | <span data-ttu-id="fd495-197">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-197">Platform</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="fd495-198">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="fd495-199">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="fd495-200">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="fd495-201">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-201">Linux and macOS</span></span> |
| <span data-ttu-id="fd495-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-203">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="fd495-204">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="fd495-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="fd495-205">System.Media</span></span>

| <span data-ttu-id="fd495-206">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-206">Member</span></span> | <span data-ttu-id="fd495-207">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-207">Platform</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-208">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="fd495-209">{1&gt;{2&gt;System.Net&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-209">System.Net</span></span>

| <span data-ttu-id="fd495-210">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-210">Member</span></span> | <span data-ttu-id="fd495-211">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-211">Platform</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="fd495-212">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="fd495-213">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-214">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-215">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-216">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-217">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-218">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-219">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-220">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-221">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-222">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="fd495-223">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-224">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-225">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-226">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-227">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-228">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="fd495-229">{1&gt;System.Net.NetworkInformation&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="fd495-230">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-230">Member</span></span> | <span data-ttu-id="fd495-231">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-231">Platform</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="fd495-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="fd495-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="fd495-233">System.Net.Sockets</span></span>

| <span data-ttu-id="fd495-234">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-234">Member</span></span> | <span data-ttu-id="fd495-235">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-235">Platform</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="fd495-236">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-236">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="fd495-237">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="fd495-237">System.Net.WebSockets</span></span>

| <span data-ttu-id="fd495-238">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-238">Member</span></span> | <span data-ttu-id="fd495-239">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-239">Platform</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="fd495-240">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-240">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="fd495-241">System.Reflection</span><span class="sxs-lookup"><span data-stu-id="fd495-241">System.Reflection</span></span>

| <span data-ttu-id="fd495-242">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-242">Member</span></span> | <span data-ttu-id="fd495-243">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-243">Platform</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-244">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-244">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-245">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-245">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-246">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="fd495-247">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-247">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-248">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-249">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="fd495-250">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-250">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="fd495-251">{1&gt;{2&gt;System.Runtime.CompilerServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-251">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="fd495-252">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-252">Member</span></span> | <span data-ttu-id="fd495-253">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-253">Platform</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="fd495-254">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-254">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="fd495-255">{1&gt;{2&gt;System.Runtime.InteropServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-255">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="fd495-256">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-256">Member</span></span> | <span data-ttu-id="fd495-257">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-257">Platform</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="fd495-258">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-258">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="fd495-259">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="fd495-260">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="fd495-261">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-261">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-262">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-262">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="fd495-263">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="fd495-264">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-264">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="fd495-265">{1&gt;System.Runtime.Serialization&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-265">System.Runtime.Serialization</span></span>

| <span data-ttu-id="fd495-266">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-266">Member</span></span> | <span data-ttu-id="fd495-267">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-267">Platform</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="fd495-268">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-268">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="fd495-269">{1&gt;{2&gt;System.Security&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-269">System.Security</span></span>

| <span data-ttu-id="fd495-270">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-270">Member</span></span> | <span data-ttu-id="fd495-271">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-271">Platform</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="fd495-272">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-272">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="fd495-273">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-273">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-274">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-274">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="fd495-275">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-275">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="fd495-276">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-276">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="fd495-277">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-277">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="fd495-278">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-278">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="fd495-279">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-279">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="fd495-280">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="fd495-281">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-281">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="fd495-282">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-282">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="fd495-283">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-283">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="fd495-284">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="fd495-285">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-285">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="fd495-286">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="fd495-286">System.Security.Claims</span></span>

| <span data-ttu-id="fd495-287">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-287">Member</span></span> | <span data-ttu-id="fd495-288">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-288">Platform</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor?displayProperty=nameWithType> | <span data-ttu-id="fd495-289">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-289">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-290">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)?displayProperty=nameWithType> | <span data-ttu-id="fd495-291">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-292">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-293">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-293">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="fd495-294">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="fd495-294">System.Security.Cryptography</span></span>

| <span data-ttu-id="fd495-295">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-295">Member</span></span> | <span data-ttu-id="fd495-296">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-296">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-297">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-297">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-298">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-298">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="fd495-299">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="fd495-300">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="fd495-301">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="fd495-302">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="fd495-303">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="fd495-304">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="fd495-305">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="fd495-306">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="fd495-307">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="fd495-308">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="fd495-309">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="fd495-310">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="fd495-311">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-311">All</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-312">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="fd495-313">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-314">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-315">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-316">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-317">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="fd495-318">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-319">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-320">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-321">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="fd495-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-322">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-323">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="fd495-324">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="fd495-325">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="fd495-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="fd495-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="fd495-327">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-327">Member</span></span> | <span data-ttu-id="fd495-328">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-328">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)?displayProperty=nameWithType> | <span data-ttu-id="fd495-329">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="fd495-330">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="fd495-331">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="fd495-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="fd495-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="fd495-333">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-333">Member</span></span> | <span data-ttu-id="fd495-334">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-334">Platform</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-335">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-336">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-337">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-337">All</span></span> |
| <span data-ttu-id="fd495-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="fd495-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="fd495-339">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="fd495-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="fd495-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="fd495-341">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-341">Member</span></span> | <span data-ttu-id="fd495-342">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-342">Platform</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-343">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="fd495-344">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="fd495-344">System.Security.Policy</span></span>

| <span data-ttu-id="fd495-345">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-345">Member</span></span> | <span data-ttu-id="fd495-346">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-346">Platform</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-347">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="fd495-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="fd495-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="fd495-349">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-349">Member</span></span> | <span data-ttu-id="fd495-350">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-350">Platform</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-351">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="fd495-352">{1&gt;System.Text.RegularExpressions&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="fd495-353">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-353">Member</span></span> | <span data-ttu-id="fd495-354">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-354">Platform</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-355">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="fd495-356">{1&gt;System.Threading&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-356">System.Threading</span></span>

| <span data-ttu-id="fd495-357">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-357">Member</span></span> | <span data-ttu-id="fd495-358">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-358">Platform</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-359">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="fd495-360">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="fd495-361">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="fd495-362">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="fd495-363">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="fd495-364">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="fd495-365">{1&gt;System.Xml&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-365">System.Xml</span></span>

| <span data-ttu-id="fd495-366">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-366">Member</span></span> | <span data-ttu-id="fd495-367">Platform</span><span class="sxs-lookup"><span data-stu-id="fd495-367">Platform</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="fd495-368">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="fd495-369">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="fd495-370">{1&gt;Todos&lt;1}</span><span class="sxs-lookup"><span data-stu-id="fd495-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="fd495-371">Veja também</span><span class="sxs-lookup"><span data-stu-id="fd495-371">See also</span></span>

- [<span data-ttu-id="fd495-372">Alterações recentes de migração do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd495-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="fd495-373">Serialização binária no .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd495-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="fd495-374">Analisador de portabilidade .NET</span><span class="sxs-lookup"><span data-stu-id="fd495-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
