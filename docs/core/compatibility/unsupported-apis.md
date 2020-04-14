---
title: APIs não suportadas no Núcleo .NET
titleSuffix: ''
description: Saiba quais APIs do .NET Framework que sempre jogam uma exceção no .NET Core.
ms.date: 12/23/2019
ms.openlocfilehash: bd3516d9480ef42b6ea89825ba64867a3ca104e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242940"
---
# <a name="apis-that-always-throw-exceptions-on-net-core"></a><span data-ttu-id="5229a-103">APIs que sempre lançam exceções no .NET Core</span><span class="sxs-lookup"><span data-stu-id="5229a-103">APIs that always throw exceptions on .NET Core</span></span>

<span data-ttu-id="5229a-104">As APIs a seguir <xref:System.PlatformNotSupportedException> sempre lançarão um no .NET Core em todas ou em um subconjunto de plataformas.</span><span class="sxs-lookup"><span data-stu-id="5229a-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET Core on all or a subset of platforms.</span></span>

<span data-ttu-id="5229a-105">Este artigo organiza os membros da API afetados por namespace.</span><span class="sxs-lookup"><span data-stu-id="5229a-105">This article organizes the affected API members by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="5229a-106">Este artigo é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="5229a-106">This article is a work-in-progress.</span></span> <span data-ttu-id="5229a-107">Não é uma lista completa de APIs que lançam exceções no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5229a-107">It is not a complete list of APIs that throw exceptions on .NET Core.</span></span>
> - <span data-ttu-id="5229a-108">Este artigo não inclui as implementações explícitas de interface para serialização binária que jogam no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5229a-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET Core.</span></span> <span data-ttu-id="5229a-109">Para obter mais informações, consulte [serialização binária no .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="5229a-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="5229a-110">Sistema</span><span class="sxs-lookup"><span data-stu-id="5229a-110">System</span></span>

| <span data-ttu-id="5229a-111">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-111">Member</span></span> | <span data-ttu-id="5229a-112">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-113">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="5229a-114">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="5229a-115">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="5229a-116">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-117">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="5229a-118">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="5229a-119">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="5229a-120">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-121">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="5229a-122">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="5229a-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="5229a-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="5229a-124">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-124">Member</span></span> | <span data-ttu-id="5229a-125">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-126">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-127">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-128">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="5229a-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="5229a-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="5229a-130">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-130">Member</span></span> | <span data-ttu-id="5229a-131">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-132">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-133">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5229a-134">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="5229a-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="5229a-135">System.Configuration</span></span>

| <span data-ttu-id="5229a-136">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-136">Member</span></span> | <span data-ttu-id="5229a-137">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="5229a-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType>(todos os membros)</span><span class="sxs-lookup"><span data-stu-id="5229a-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="5229a-139">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="5229a-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="5229a-140">System.Console</span></span>

| <span data-ttu-id="5229a-141">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-141">Member</span></span> | <span data-ttu-id="5229a-142">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="5229a-143">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-143">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-145">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-145">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-147">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-147">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-148"><xref:System.Console.CursorSize?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-149">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-149">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType>(obter apenas)</span><span class="sxs-lookup"><span data-stu-id="5229a-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="5229a-151">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-152">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-153">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-154">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-154">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-155"><xref:System.Console.Title?displayProperty=nameWithType>(obter apenas)</span><span class="sxs-lookup"><span data-stu-id="5229a-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="5229a-156">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-156">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-158">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-158">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-160">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-160">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-161"><xref:System.Console.WindowTop?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-162">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-162">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-164">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="5229a-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="5229a-165">System.Data.Common</span></span>

| <span data-ttu-id="5229a-166">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-166">Member</span></span> | <span data-ttu-id="5229a-167">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="5229a-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType>(lançamentos) <xref:System.NotSupportedException></span><span class="sxs-lookup"><span data-stu-id="5229a-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="5229a-169">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="5229a-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="5229a-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="5229a-171">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-171">Member</span></span> | <span data-ttu-id="5229a-172">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="5229a-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-174">Linux</span><span class="sxs-lookup"><span data-stu-id="5229a-174">Linux</span></span> |
| <span data-ttu-id="5229a-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-176">Linux</span><span class="sxs-lookup"><span data-stu-id="5229a-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="5229a-177">macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="5229a-178">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-179">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="5229a-180">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="5229a-181">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="5229a-182">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="5229a-183">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-183">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-185">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-185">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType>(obter apenas)</span><span class="sxs-lookup"><span data-stu-id="5229a-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="5229a-187">macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-187">macOS</span></span> |
| <span data-ttu-id="5229a-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-189">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="5229a-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="5229a-190">System.IO</span></span>

| <span data-ttu-id="5229a-191">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-191">Member</span></span> | <span data-ttu-id="5229a-192">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-193">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-194">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="5229a-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="5229a-195">System.IO.Pipes</span></span>

| <span data-ttu-id="5229a-196">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-196">Member</span></span> | <span data-ttu-id="5229a-197">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="5229a-198">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="5229a-199">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="5229a-200">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="5229a-201">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-201">Linux and macOS</span></span> |
| <span data-ttu-id="5229a-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-203">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="5229a-204">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="5229a-205">System.Media</span><span class="sxs-lookup"><span data-stu-id="5229a-205">System.Media</span></span>

| <span data-ttu-id="5229a-206">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-206">Member</span></span> | <span data-ttu-id="5229a-207">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-208">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="5229a-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="5229a-209">System.Net</span></span>

| <span data-ttu-id="5229a-210">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-210">Member</span></span> | <span data-ttu-id="5229a-211">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="5229a-212">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="5229a-213">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-214">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-215">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-216">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-217">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-218">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-219">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-220">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-221">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-222">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="5229a-223">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-224">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-225">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-226">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-227">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-228">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="5229a-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="5229a-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="5229a-230">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-230">Member</span></span> | <span data-ttu-id="5229a-231">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-232">Janelas (UWP)</span><span class="sxs-lookup"><span data-stu-id="5229a-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="5229a-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="5229a-233">System.Net.Sockets</span></span>

| <span data-ttu-id="5229a-234">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-234">Member</span></span> | <span data-ttu-id="5229a-235">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="5229a-236">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="5229a-237">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="5229a-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="5229a-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="5229a-239">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-239">Member</span></span> | <span data-ttu-id="5229a-240">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="5229a-241">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="5229a-242">{1&gt;System.Reflection&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5229a-242">System.Reflection</span></span>

| <span data-ttu-id="5229a-243">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-243">Member</span></span> | <span data-ttu-id="5229a-244">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-245">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-246">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-247">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5229a-248">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="5229a-249">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-250">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="5229a-251">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="5229a-252">{1&gt;{2&gt;System.Runtime.CompilerServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5229a-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="5229a-253">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-253">Member</span></span> | <span data-ttu-id="5229a-254">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="5229a-255">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="5229a-256">{1&gt;{2&gt;System.Runtime.InteropServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5229a-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="5229a-257">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-257">Member</span></span> | <span data-ttu-id="5229a-258">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5229a-259">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="5229a-260">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="5229a-261">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="5229a-262">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-263">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="5229a-264">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="5229a-265">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="5229a-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="5229a-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="5229a-267">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-267">Member</span></span> | <span data-ttu-id="5229a-268">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="5229a-269">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="5229a-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="5229a-270">System.Security</span></span>

| <span data-ttu-id="5229a-271">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-271">Member</span></span> | <span data-ttu-id="5229a-272">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="5229a-273">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="5229a-274">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-275">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="5229a-276">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="5229a-277">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="5229a-278">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="5229a-279">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="5229a-280">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="5229a-281">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="5229a-282">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="5229a-283">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="5229a-284">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="5229a-285">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="5229a-286">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="5229a-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="5229a-287">System.Security.Claims</span></span>

| <span data-ttu-id="5229a-288">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-288">Member</span></span> | <span data-ttu-id="5229a-289">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor> | <span data-ttu-id="5229a-290">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-291">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="5229a-292">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-293">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-294">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="5229a-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="5229a-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="5229a-296">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-296">Member</span></span> | <span data-ttu-id="5229a-297">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-298">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="5229a-299">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="5229a-300">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="5229a-301">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="5229a-302">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="5229a-303">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="5229a-304">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="5229a-305">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="5229a-306">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="5229a-307">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="5229a-308">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="5229a-309">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="5229a-310">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="5229a-311">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="5229a-312">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="5229a-313">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-314">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-315">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-316">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-317">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="5229a-318">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-319">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-320">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-321">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="5229a-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-322">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-323">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="5229a-324">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="5229a-325">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="5229a-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="5229a-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="5229a-327">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-327">Member</span></span> | <span data-ttu-id="5229a-328">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="5229a-329">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignedCms.ComputeSignature(System.Security.Cryptography.Pkcs.CmsSigner,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="5229a-330">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-330">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="5229a-331">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-331">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="5229a-332">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="5229a-332">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="5229a-333">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-333">Member</span></span> | <span data-ttu-id="5229a-334">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-334">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-335">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-336">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-336">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-337">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-337">All</span></span> |
| <span data-ttu-id="5229a-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType>(apenas definido)</span><span class="sxs-lookup"><span data-stu-id="5229a-338"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="5229a-339">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-339">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="5229a-340">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="5229a-340">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="5229a-341">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-341">Member</span></span> | <span data-ttu-id="5229a-342">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-342">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-343">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-343">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="5229a-344">System.Security.Policy</span><span class="sxs-lookup"><span data-stu-id="5229a-344">System.Security.Policy</span></span>

| <span data-ttu-id="5229a-345">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-345">Member</span></span> | <span data-ttu-id="5229a-346">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-346">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-347">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-347">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="5229a-348">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="5229a-348">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="5229a-349">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-349">Member</span></span> | <span data-ttu-id="5229a-350">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-350">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="5229a-351">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-351">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="5229a-352">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="5229a-352">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="5229a-353">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-353">Member</span></span> | <span data-ttu-id="5229a-354">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-354">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-355">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-355">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="5229a-356">System.Threading</span><span class="sxs-lookup"><span data-stu-id="5229a-356">System.Threading</span></span>

| <span data-ttu-id="5229a-357">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-357">Member</span></span> | <span data-ttu-id="5229a-358">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-358">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-359">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-359">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="5229a-360">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-360">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="5229a-361">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-361">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="5229a-362">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-362">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="5229a-363">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-363">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="5229a-364">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-364">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="5229a-365">System.Xml</span><span class="sxs-lookup"><span data-stu-id="5229a-365">System.Xml</span></span>

| <span data-ttu-id="5229a-366">Membro</span><span class="sxs-lookup"><span data-stu-id="5229a-366">Member</span></span> | <span data-ttu-id="5229a-367">Plataformas que jogam</span><span class="sxs-lookup"><span data-stu-id="5229a-367">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="5229a-368">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="5229a-369">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-369">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="5229a-370">Todos</span><span class="sxs-lookup"><span data-stu-id="5229a-370">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="5229a-371">Confira também</span><span class="sxs-lookup"><span data-stu-id="5229a-371">See also</span></span>

- [<span data-ttu-id="5229a-372">Alterações de separação de migração do .NET Framework para .NET Core</span><span class="sxs-lookup"><span data-stu-id="5229a-372">Breaking changes for migration from .NET Framework to .NET Core</span></span>](../compatibility/fx-core.md)
- [<span data-ttu-id="5229a-373">Serialização binária no .NET Core</span><span class="sxs-lookup"><span data-stu-id="5229a-373">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="5229a-374">Analisador de portabilidade .NET</span><span class="sxs-lookup"><span data-stu-id="5229a-374">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
