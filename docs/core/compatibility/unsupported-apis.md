---
title: APIs sem suporte no .NET Core
titleSuffix: ''
description: Saiba quais APIs do .NET Framework que sempre lançam uma exceção no .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: 94f334d7e4b7daf407f489ba274172ced9eefa81
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414429"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="a0182-103">APIs que sempre lançam exceções no .NET Core</span><span class="sxs-lookup"><span data-stu-id="a0182-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="a0182-104">As APIs a seguir sempre lançarão um <xref:System.PlatformNotSupportedException> no .NET Core em todos ou em um subconjunto de plataformas.</span><span class="sxs-lookup"><span data-stu-id="a0182-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="a0182-105">Este artigo organiza os membros de API afetados por namespace.</span><span class="sxs-lookup"><span data-stu-id="a0182-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="a0182-106">Este artigo é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="a0182-106">This article is a work-in-progress.</span></span> <span data-ttu-id="a0182-107">Não é uma lista completa de APIs que lançam exceções no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a0182-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="a0182-108">Este artigo não inclui as implementações de interface explícitas para serialização binária que lançam no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a0182-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="a0182-109">Para obter mais informações, consulte [serialização binária no .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="a0182-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="a0182-110">Sistema</span><span class="sxs-lookup"><span data-stu-id="a0182-110">System</span></span>

| <span data-ttu-id="a0182-111">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-111">Member</span></span> | <span data-ttu-id="a0182-112">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-113">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="a0182-114">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="a0182-115">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="a0182-116">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-117">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="a0182-118">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="a0182-119">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="a0182-120">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-121">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a0182-122">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="a0182-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="a0182-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="a0182-124">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-124">Member</span></span> | <span data-ttu-id="a0182-125">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-126">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-127">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-128">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="a0182-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="a0182-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="a0182-130">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-130">Member</span></span> | <span data-ttu-id="a0182-131">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-132">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-133">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a0182-134">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="a0182-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="a0182-135">System.Configuration</span></span>

| <span data-ttu-id="a0182-136">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-136">Member</span></span> | <span data-ttu-id="a0182-137">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a0182-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="a0182-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="a0182-139">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="a0182-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="a0182-140">System.Console</span></span>

| <span data-ttu-id="a0182-141">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-141">Member</span></span> | <span data-ttu-id="a0182-142">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="a0182-143">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-143">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-145">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-145">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-147">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-147">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-149">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-149">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="a0182-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a0182-151">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-152">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-153">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-154">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-154">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-155"><xref:System.Console.Title?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="a0182-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a0182-156">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-156">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-158">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-158">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-160">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-160">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-162">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-162">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-164">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="a0182-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="a0182-165">System.Data.Common</span></span>

| <span data-ttu-id="a0182-166">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-166">Member</span></span> | <span data-ttu-id="a0182-167">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a0182-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (gera <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="a0182-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="a0182-169">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="a0182-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="a0182-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="a0182-171">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-171">Member</span></span> | <span data-ttu-id="a0182-172">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="a0182-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-174">Linux</span><span class="sxs-lookup"><span data-stu-id="a0182-174">Linux</span></span> |
| <span data-ttu-id="a0182-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-176">Linux</span><span class="sxs-lookup"><span data-stu-id="a0182-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="a0182-177">macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="a0182-178">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-179">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="a0182-180">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="a0182-181">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="a0182-182">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="a0182-183">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-183">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-185">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-185">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="a0182-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="a0182-187">macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-187">macOS</span></span> |
| <span data-ttu-id="a0182-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-189">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="a0182-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="a0182-190">System.IO</span></span>

| <span data-ttu-id="a0182-191">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-191">Member</span></span> | <span data-ttu-id="a0182-192">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-193">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-194">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="a0182-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="a0182-195">System.IO.Pipes</span></span>

| <span data-ttu-id="a0182-196">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-196">Member</span></span> | <span data-ttu-id="a0182-197">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="a0182-198">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="a0182-199">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="a0182-200">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="a0182-201">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-201">Linux and macOS</span></span> |
| <span data-ttu-id="a0182-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-203">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="a0182-204">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="a0182-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="a0182-205">System.Media</span></span>

| <span data-ttu-id="a0182-206">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-206">Member</span></span> | <span data-ttu-id="a0182-207">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-208">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="a0182-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="a0182-209">System.Net</span></span>

| <span data-ttu-id="a0182-210">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-210">Member</span></span> | <span data-ttu-id="a0182-211">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="a0182-212">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="a0182-213">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-214">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-215">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-216">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-217">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-218">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-219">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-220">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-221">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-222">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="a0182-223">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-224">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-225">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-226">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-227">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-228">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="a0182-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="a0182-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="a0182-230">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-230">Member</span></span> | <span data-ttu-id="a0182-231">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="a0182-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="a0182-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="a0182-233">System.Net.Sockets</span></span>

| <span data-ttu-id="a0182-234">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-234">Member</span></span> | <span data-ttu-id="a0182-235">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="a0182-236">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="a0182-237">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="a0182-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="a0182-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="a0182-239">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-239">Member</span></span> | <span data-ttu-id="a0182-240">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="a0182-241">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="a0182-242">{1&gt;System.Reflection&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a0182-242">System.Reflection</span></span>

| <span data-ttu-id="a0182-243">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-243">Member</span></span> | <span data-ttu-id="a0182-244">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-245">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-246">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-247">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a0182-248">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="a0182-249">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-250">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="a0182-251">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="a0182-252">{1&gt;{2&gt;System.Runtime.CompilerServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a0182-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="a0182-253">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-253">Member</span></span> | <span data-ttu-id="a0182-254">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="a0182-255">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="a0182-256">{1&gt;{2&gt;System.Runtime.InteropServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="a0182-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="a0182-257">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-257">Member</span></span> | <span data-ttu-id="a0182-258">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a0182-259">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="a0182-260">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="a0182-261">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="a0182-262">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-263">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="a0182-264">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="a0182-265">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="a0182-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="a0182-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="a0182-267">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-267">Member</span></span> | <span data-ttu-id="a0182-268">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="a0182-269">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="a0182-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="a0182-270">System.Security</span></span>

| <span data-ttu-id="a0182-271">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-271">Member</span></span> | <span data-ttu-id="a0182-272">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="a0182-273">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="a0182-274">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-275">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="a0182-276">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="a0182-277">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="a0182-278">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="a0182-279">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="a0182-280">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="a0182-281">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="a0182-282">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="a0182-283">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="a0182-284">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="a0182-285">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="a0182-286">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="a0182-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="a0182-287">System.Security.Claims</span></span>

| <span data-ttu-id="a0182-288">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-288">Member</span></span> | <span data-ttu-id="a0182-289">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="a0182-290">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-291">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="a0182-292">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-293">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-294">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="a0182-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="a0182-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="a0182-296">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-296">Member</span></span> | <span data-ttu-id="a0182-297">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-298">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="a0182-299">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="a0182-300">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="a0182-301">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="a0182-302">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="a0182-303">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="a0182-304">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="a0182-305">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="a0182-306">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="a0182-307">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="a0182-308">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="a0182-309">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="a0182-310">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="a0182-311">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a0182-312">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="a0182-313">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-314">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-315">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-316">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-317">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a0182-318">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-319">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-320">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-321">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="a0182-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-322">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-323">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="a0182-324">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="a0182-325">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="a0182-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="a0182-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="a0182-327">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-327">Member</span></span> | <span data-ttu-id="a0182-328">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="a0182-329">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="a0182-330">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="a0182-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="a0182-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="a0182-332">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-332">Member</span></span> | <span data-ttu-id="a0182-333">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-334">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-335">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-336">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-336">All</span></span> |
| <span data-ttu-id="a0182-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="a0182-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="a0182-338">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="a0182-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="a0182-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="a0182-340">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-340">Member</span></span> | <span data-ttu-id="a0182-341">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-342">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="a0182-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="a0182-343">System.Security.Policy</span></span>

| <span data-ttu-id="a0182-344">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-344">Member</span></span> | <span data-ttu-id="a0182-345">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-346">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="a0182-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="a0182-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="a0182-348">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-348">Member</span></span> | <span data-ttu-id="a0182-349">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="a0182-350">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="a0182-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="a0182-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="a0182-352">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-352">Member</span></span> | <span data-ttu-id="a0182-353">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-354">Tudo</span><span class="sxs-lookup"><span data-stu-id="a0182-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="a0182-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="a0182-355">System.Threading</span></span>

| <span data-ttu-id="a0182-356">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-356">Member</span></span> | <span data-ttu-id="a0182-357">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-358">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="a0182-359">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="a0182-360">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="a0182-361">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="a0182-362">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="a0182-363">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="a0182-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="a0182-364">System.Xml</span></span>

| <span data-ttu-id="a0182-365">Membro</span><span class="sxs-lookup"><span data-stu-id="a0182-365">Member</span></span> | <span data-ttu-id="a0182-366">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="a0182-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="a0182-367">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="a0182-368">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="a0182-369">Todos</span><span class="sxs-lookup"><span data-stu-id="a0182-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="a0182-370">Confira também</span><span class="sxs-lookup"><span data-stu-id="a0182-370">See also</span></span>

- [<span data-ttu-id="a0182-371">Alterações recentes de migração do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="a0182-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="a0182-372">Serialização binária no .NET Core</span><span class="sxs-lookup"><span data-stu-id="a0182-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="a0182-373">Analisador de portabilidade .NET</span><span class="sxs-lookup"><span data-stu-id="a0182-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
