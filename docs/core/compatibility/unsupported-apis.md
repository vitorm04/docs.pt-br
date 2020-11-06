---
title: APIs sem suporte no .NET Core e no .NET 5 +
titleSuffix: ''
description: Saiba quais APIs do .NET sempre geram uma exceção no .NET Core e no .NET 5,0 e versões posteriores.
ms.date: 10/13/2020
ms.openlocfilehash: 51d73557a48910d9cb1c4d3cdced34dfe4d849d8
ms.sourcegitcommit: 6bef8abde346c59771a35f4f76bf037ff61c5ba3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/06/2020
ms.locfileid: "94329775"
---
# <a name="apis-that-always-throw-exceptions-on-net-core-and-net-5"></a><span data-ttu-id="bb99c-103">APIs que sempre lançam exceções no .NET Core e no .NET 5 +</span><span class="sxs-lookup"><span data-stu-id="bb99c-103">APIs that always throw exceptions on .NET Core and .NET 5+</span></span>

<span data-ttu-id="bb99c-104">As APIs a seguir sempre lançarão um <xref:System.PlatformNotSupportedException> no .net 5,0 e em versões posteriores (incluindo todas as versões do .NET Core) em todos os ou em um subconjunto de plataformas.</span><span class="sxs-lookup"><span data-stu-id="bb99c-104">The following APIs will always throw a <xref:System.PlatformNotSupportedException> on .NET 5.0 and later versions (including all versions of .NET Core) on all or a subset of platforms.</span></span>

<span data-ttu-id="bb99c-105">Este artigo organiza as APIs afetadas por namespace.</span><span class="sxs-lookup"><span data-stu-id="bb99c-105">This article organizes the affected APIs by namespace.</span></span>

> [!NOTE]
>
> - <span data-ttu-id="bb99c-106">Este artigo é um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="bb99c-106">This article is a work-in-progress.</span></span> <span data-ttu-id="bb99c-107">Não é uma lista completa de APIs que lançam exceções no .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="bb99c-107">It is not a complete list of APIs that throw exceptions on .NET 5+.</span></span>
> - <span data-ttu-id="bb99c-108">Este artigo não inclui as implementações de interface explícitas para serialização binária que lançam no .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="bb99c-108">This article does not include the explicit interface implementations for binary serialization that throw on .NET 5+.</span></span> <span data-ttu-id="bb99c-109">Para obter mais informações, consulte [serialização binária no .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span><span class="sxs-lookup"><span data-stu-id="bb99c-109">For more information, see [Binary serialization in .NET Core](../../standard/serialization/binary-serialization.md#net-core).</span></span>

## <a name="system"></a><span data-ttu-id="bb99c-110">Sistema</span><span class="sxs-lookup"><span data-stu-id="bb99c-110">System</span></span>

| <span data-ttu-id="bb99c-111">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-111">Member</span></span> | <span data-ttu-id="bb99c-112">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-112">Platforms that throw</span></span> |
| - | - |
| <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-113">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-113">All</span></span> |
| <xref:System.AppDomain.ExecuteAssembly(System.String,System.String[],System.Byte[],System.Configuration.Assemblies.AssemblyHashAlgorithm)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-114">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-114">All</span></span> |
| <xref:System.Console.CapsLock?displayProperty=nameWithType> | <span data-ttu-id="bb99c-115">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-115">Linux and macOS</span></span> |
| <xref:System.Console.NumberLock?displayProperty=nameWithType> | <span data-ttu-id="bb99c-116">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-116">Linux and macOS</span></span> |
| <xref:System.Delegate.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-117">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-117">All</span></span> |
| <xref:System.Exception.SerializeObjectState?displayProperty=nameWithType> | <span data-ttu-id="bb99c-118">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-118">All</span></span> |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="bb99c-119">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-119">All</span></span> |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | <span data-ttu-id="bb99c-120">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-120">All</span></span> |
| <xref:System.OperatingSystem.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-121">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-121">All</span></span> |
| <xref:System.Type.ReflectionOnlyGetType(System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-122">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-122">All</span></span> |

## <a name="systemcodedomcompiler"></a><span data-ttu-id="bb99c-123">System.CodeDom.Compiler</span><span class="sxs-lookup"><span data-stu-id="bb99c-123">System.CodeDom.Compiler</span></span>

| <span data-ttu-id="bb99c-124">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-124">Member</span></span> | <span data-ttu-id="bb99c-125">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-125">Platforms that throw</span></span> |
| - | - |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromDom%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-126">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-126">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromFile%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-127">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-127">All</span></span> |
| <xref:System.CodeDom.Compiler.CodeDomProvider.CompileAssemblyFromSource%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-128">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-128">All</span></span> |

## <a name="systemcollectionsspecialized"></a><span data-ttu-id="bb99c-129">System.Collections.Specialized</span><span class="sxs-lookup"><span data-stu-id="bb99c-129">System.Collections.Specialized</span></span>

| <span data-ttu-id="bb99c-130">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-130">Member</span></span> | <span data-ttu-id="bb99c-131">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-131">Platforms that throw</span></span> |
| - | - |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-132">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-132">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-133">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-133">All</span></span> |
| <xref:System.Collections.Specialized.NameObjectCollectionBase.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-134">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-134">All</span></span> |

## <a name="systemconfiguration"></a><span data-ttu-id="bb99c-135">System.Configuration</span><span class="sxs-lookup"><span data-stu-id="bb99c-135">System.Configuration</span></span>

| <span data-ttu-id="bb99c-136">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-136">Member</span></span> | <span data-ttu-id="bb99c-137">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-137">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="bb99c-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (todos os membros)</span><span class="sxs-lookup"><span data-stu-id="bb99c-138"><xref:System.Configuration.RsaProtectedConfigurationProvider?displayProperty=nameWithType> (all members)</span></span> | <span data-ttu-id="bb99c-139">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-139">All</span></span> |

## <a name="systemconsole"></a><span data-ttu-id="bb99c-140">System.Console</span><span class="sxs-lookup"><span data-stu-id="bb99c-140">System.Console</span></span>

| <span data-ttu-id="bb99c-141">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-141">Member</span></span> | <span data-ttu-id="bb99c-142">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-142">Platforms that throw</span></span> |
| - | - |
| <xref:System.Console.Beep?displayProperty=nameWithType> | <span data-ttu-id="bb99c-143">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-143">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-144"><xref:System.Console.BufferHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-145">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-145">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-146"><xref:System.Console.BufferWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-147">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-147">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-148"><xref:System.Console.CursorSize?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-149">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-149">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="bb99c-150"><xref:System.Console.CursorVisible?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="bb99c-151">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-151">Linux and macOS</span></span> |
| <xref:System.Console.MoveBufferArea%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-152">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-152">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowPosition%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-153">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-153">Linux and macOS</span></span> |
| <xref:System.Console.SetWindowSize%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-154">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-154">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-155"><xref:System.Console.Title?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="bb99c-155"><xref:System.Console.Title?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="bb99c-156">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-156">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-157"><xref:System.Console.WindowHeight?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-158">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-158">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-159"><xref:System.Console.WindowLeft?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-160">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-160">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-161"><xref:System.Console.WindowTop?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-162">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-162">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-163"><xref:System.Console.WindowWidth?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-164">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-164">Linux and macOS</span></span> |

## <a name="systemdatacommon"></a><span data-ttu-id="bb99c-165">System.Data.Common</span><span class="sxs-lookup"><span data-stu-id="bb99c-165">System.Data.Common</span></span>

| <span data-ttu-id="bb99c-166">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-166">Member</span></span> | <span data-ttu-id="bb99c-167">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-167">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="bb99c-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (gera <xref:System.NotSupportedException> )</span><span class="sxs-lookup"><span data-stu-id="bb99c-168"><xref:System.Data.Common.DbDataReader.GetSchemaTable%2A?displayProperty=nameWithType> (throws <xref:System.NotSupportedException>)</span></span> | <span data-ttu-id="bb99c-169">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-169">All</span></span> |

## <a name="systemdiagnosticsprocess"></a><span data-ttu-id="bb99c-170">System.Diagnostics.Process</span><span class="sxs-lookup"><span data-stu-id="bb99c-170">System.Diagnostics.Process</span></span>

| <span data-ttu-id="bb99c-171">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-171">Member</span></span> | <span data-ttu-id="bb99c-172">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-172">Platforms that throw</span></span> |
| - | - |
| <span data-ttu-id="bb99c-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-173"><xref:System.Diagnostics.Process.MaxWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-174">Linux</span><span class="sxs-lookup"><span data-stu-id="bb99c-174">Linux</span></span> |
| <span data-ttu-id="bb99c-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-175"><xref:System.Diagnostics.Process.MinWorkingSet?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-176">Linux</span><span class="sxs-lookup"><span data-stu-id="bb99c-176">Linux</span></span> |
| <xref:System.Diagnostics.Process.ProcessorAffinity?displayProperty=nameWithType> | <span data-ttu-id="bb99c-177">macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-177">macOS</span></span> |
| <xref:System.Diagnostics.Process.MainWindowHandle?displayProperty=nameWithType> | <span data-ttu-id="bb99c-178">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-178">Linux and macOS</span></span> |
| <xref:System.Diagnostics.Process.Start%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-179">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-179">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.UserName?displayProperty=nameWithType> | <span data-ttu-id="bb99c-180">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-180">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.PasswordInClearText?displayProperty=nameWithType> | <span data-ttu-id="bb99c-181">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-181">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.Domain?displayProperty=nameWithType> | <span data-ttu-id="bb99c-182">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-182">Linux and macOS</span></span> |
| <xref:System.Diagnostics.ProcessStartInfo.LoadUserProfile?displayProperty=nameWithType> | <span data-ttu-id="bb99c-183">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-183">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-184"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-185">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-185">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (somente Get)</span><span class="sxs-lookup"><span data-stu-id="bb99c-186"><xref:System.Diagnostics.ProcessThread.BasePriority?displayProperty=nameWithType> (get only)</span></span> | <span data-ttu-id="bb99c-187">macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-187">macOS</span></span> |
| <span data-ttu-id="bb99c-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-188"><xref:System.Diagnostics.ProcessThread.ProcessorAffinity?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-189">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-189">Linux and macOS</span></span> |

## <a name="systemio"></a><span data-ttu-id="bb99c-190">System.IO</span><span class="sxs-lookup"><span data-stu-id="bb99c-190">System.IO</span></span>

| <span data-ttu-id="bb99c-191">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-191">Member</span></span> | <span data-ttu-id="bb99c-192">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-192">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.FileSystemInfo.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-193">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-193">All</span></span> |
| <xref:System.IO.FileSystemInfo.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-194">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-194">All</span></span> |

## <a name="systemiopipes"></a><span data-ttu-id="bb99c-195">System.IO.Pipes</span><span class="sxs-lookup"><span data-stu-id="bb99c-195">System.IO.Pipes</span></span>

| <span data-ttu-id="bb99c-196">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-196">Member</span></span> | <span data-ttu-id="bb99c-197">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-197">Platforms that throw</span></span> |
| - | - |
| <xref:System.IO.Pipes.NamedPipeClientStream.NumberOfServerInstances?displayProperty=nameWithType> | <span data-ttu-id="bb99c-198">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-198">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.NamedPipeServerStream.GetImpersonationUserName?displayProperty=nameWithType> | <span data-ttu-id="bb99c-199">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-199">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.InBufferSize?displayProperty=nameWithType> | <span data-ttu-id="bb99c-200">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-200">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.OutBufferSize?displayProperty=nameWithType> | <span data-ttu-id="bb99c-201">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-201">Linux and macOS</span></span> |
| <span data-ttu-id="bb99c-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-202"><xref:System.IO.Pipes.PipeStream.ReadMode?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-203">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-203">Linux and macOS</span></span> |
| <xref:System.IO.Pipes.PipeStream.WaitForPipeDrain?displayProperty=nameWithType> | <span data-ttu-id="bb99c-204">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-204">Linux and macOS</span></span> |

## <a name="systemmedia"></a><span data-ttu-id="bb99c-205">System. Media</span><span class="sxs-lookup"><span data-stu-id="bb99c-205">System.Media</span></span>

| <span data-ttu-id="bb99c-206">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-206">Member</span></span> | <span data-ttu-id="bb99c-207">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-207">Platforms that throw</span></span> |
| - | - |
| <xref:System.Media.SoundPlayer.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-208">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-208">All</span></span> |

## <a name="systemnet"></a><span data-ttu-id="bb99c-209">System.Net</span><span class="sxs-lookup"><span data-stu-id="bb99c-209">System.Net</span></span>

| <span data-ttu-id="bb99c-210">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-210">Member</span></span> | <span data-ttu-id="bb99c-211">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-211">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.AuthenticationManager.Authenticate(System.String,System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-212">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-212">All</span></span> |
| <xref:System.Net.AuthenticationManager.PreAuthenticate(System.Net.WebRequest,System.Net.ICredentials)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-213">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-213">All</span></span> |
| <xref:System.Net.FileWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-214">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-214">All</span></span> |
| <xref:System.Net.FileWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-215">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-215">All</span></span> |
| <xref:System.Net.FileWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-216">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-216">All</span></span> |
| <xref:System.Net.FileWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-217">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-217">All</span></span> |
| <xref:System.Net.HttpWebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-218">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-218">All</span></span> |
| <xref:System.Net.HttpWebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-219">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-219">All</span></span> |
| <xref:System.Net.HttpWebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-220">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-220">All</span></span> |
| <xref:System.Net.HttpWebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-221">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-221">All</span></span> |
| <xref:System.Net.WebProxy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-222">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-222">All</span></span> |
| <xref:System.Net.WebProxy.GetDefaultProxy?displayProperty=nameWithType> | <span data-ttu-id="bb99c-223">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-223">All</span></span> |
| <xref:System.Net.WebProxy.GetObjectData%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-224">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-224">All</span></span> |
| <xref:System.Net.WebRequest.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-225">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-225">All</span></span> |
| <xref:System.Net.WebRequest.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-226">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-226">All</span></span> |
| <xref:System.Net.WebResponse.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-227">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-227">All</span></span> |
| <xref:System.Net.WebResponse.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-228">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-228">All</span></span> |

## <a name="systemnetnetworkinformation"></a><span data-ttu-id="bb99c-229">System.Net.NetworkInformation</span><span class="sxs-lookup"><span data-stu-id="bb99c-229">System.Net.NetworkInformation</span></span>

| <span data-ttu-id="bb99c-230">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-230">Member</span></span> | <span data-ttu-id="bb99c-231">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-231">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.NetworkInformation.Ping.Send%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-232">Windows (UWP)</span><span class="sxs-lookup"><span data-stu-id="bb99c-232">Windows (UWP)</span></span> |

## <a name="systemnetsockets"></a><span data-ttu-id="bb99c-233">System.Net.Sockets</span><span class="sxs-lookup"><span data-stu-id="bb99c-233">System.Net.Sockets</span></span>

| <span data-ttu-id="bb99c-234">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-234">Member</span></span> | <span data-ttu-id="bb99c-235">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-235">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.Sockets.Socket.%23ctor(System.Net.Sockets.SocketInformation)> | <span data-ttu-id="bb99c-236">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-236">All</span></span> |
| <xref:System.Net.Sockets.Socket.DuplicateAndClose(System.Int32)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-237">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-237">All</span></span> |

## <a name="systemnetwebsockets"></a><span data-ttu-id="bb99c-238">System.Net.WebSockets</span><span class="sxs-lookup"><span data-stu-id="bb99c-238">System.Net.WebSockets</span></span>

| <span data-ttu-id="bb99c-239">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-239">Member</span></span> | <span data-ttu-id="bb99c-240">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-240">Platforms that throw</span></span> |
| - | - |
| <xref:System.Net.WebSockets.WebSocket.RegisterPrefixes?displayProperty=nameWithType> | <span data-ttu-id="bb99c-241">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-241">All</span></span> |

## <a name="systemreflection"></a><span data-ttu-id="bb99c-242">{1&gt;System.Reflection&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bb99c-242">System.Reflection</span></span>

| <span data-ttu-id="bb99c-243">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-243">Member</span></span> | <span data-ttu-id="bb99c-244">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-244">Platforms that throw</span></span> |
| - | - |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-245">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-245">All</span></span> |
| <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom(System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-246">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-246">All</span></span> |
| <xref:System.Reflection.AssemblyName.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-247">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-247">All</span></span> |
| <xref:System.Reflection.AssemblyName.OnDeserialization(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-248">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-248">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.String)> | <span data-ttu-id="bb99c-249">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-249">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-250">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-250">All</span></span> |
| <xref:System.Reflection.StrongNameKeyPair.PublicKey?displayProperty=nameWithType> | <span data-ttu-id="bb99c-251">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-251">All</span></span> |

## <a name="systemruntimecompilerservices"></a><span data-ttu-id="bb99c-252">{1&gt;{2&gt;System.Runtime.CompilerServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bb99c-252">System.Runtime.CompilerServices</span></span>

| <span data-ttu-id="bb99c-253">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-253">Member</span></span> | <span data-ttu-id="bb99c-254">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-254">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator?displayProperty=nameWithType> | <span data-ttu-id="bb99c-255">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-255">All</span></span> |

## <a name="systemruntimeinteropservices"></a><span data-ttu-id="bb99c-256">{1&gt;{2&gt;System.Runtime.InteropServices&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="bb99c-256">System.Runtime.InteropServices</span></span>

| <span data-ttu-id="bb99c-257">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-257">Member</span></span> | <span data-ttu-id="bb99c-258">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-258">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.InteropServices.Marshal.GetIDispatchForObject(System.Object)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-259">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-259">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.SystemConfigurationFile?displayProperty=nameWithType> | <span data-ttu-id="bb99c-260">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-260">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsIntPtr(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-261">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-261">All</span></span> |
| <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeInterfaceAsObject(System.Guid,System.Guid)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-262">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-262">All</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.StringToHString(System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-263">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-263">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.PtrToStringHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-264">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-264">Linux and macOS</span></span> |
| <xref:System.Runtime.InteropServices.WindowsRuntime.WindowsRuntimeMarshal.FreeHString(System.IntPtr)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-265">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-265">Linux and macOS</span></span> |

## <a name="systemruntimeserialization"></a><span data-ttu-id="bb99c-266">System.Runtime.Serialization</span><span class="sxs-lookup"><span data-stu-id="bb99c-266">System.Runtime.Serialization</span></span>

| <span data-ttu-id="bb99c-267">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-267">Member</span></span> | <span data-ttu-id="bb99c-268">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-268">Platforms that throw</span></span> |
| - | - |
| <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas?displayProperty=nameWithType> | <span data-ttu-id="bb99c-269">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-269">All</span></span> |

## <a name="systemsecurity"></a><span data-ttu-id="bb99c-270">System.Security</span><span class="sxs-lookup"><span data-stu-id="bb99c-270">System.Security</span></span>

| <span data-ttu-id="bb99c-271">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-271">Member</span></span> | <span data-ttu-id="bb99c-272">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-272">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.CodeAccessPermission.Deny?displayProperty=nameWithType> | <span data-ttu-id="bb99c-273">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-273">All</span></span> |
| <xref:System.Security.CodeAccessPermission.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="bb99c-274">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-274">All</span></span> |
| <xref:System.Security.PermissionSet.ConvertPermissionSet(System.String,System.Byte[],System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-275">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-275">All</span></span> |
| <xref:System.Security.PermissionSet.Deny?displayProperty=nameWithType> | <span data-ttu-id="bb99c-276">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-276">All</span></span> |
| <xref:System.Security.PermissionSet.PermitOnly?displayProperty=nameWithType> | <span data-ttu-id="bb99c-277">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-277">All</span></span> |
| <xref:System.Security.SecurityContext.Capture?displayProperty=nameWithType> | <span data-ttu-id="bb99c-278">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-278">All</span></span> |
| <xref:System.Security.SecurityContext.CreateCopy?displayProperty=nameWithType> | <span data-ttu-id="bb99c-279">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-279">All</span></span> |
| <xref:System.Security.SecurityContext.Dispose?displayProperty=nameWithType> | <span data-ttu-id="bb99c-280">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-280">All</span></span> |
| <xref:System.Security.SecurityContext.IsFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="bb99c-281">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-281">All</span></span> |
| <xref:System.Security.SecurityContext.IsWindowsIdentityFlowSuppressed?displayProperty=nameWithType> | <span data-ttu-id="bb99c-282">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-282">All</span></span> |
| <xref:System.Security.SecurityContext.RestoreFlow?displayProperty=nameWithType> | <span data-ttu-id="bb99c-283">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-283">All</span></span> |
| <xref:System.Security.SecurityContext.Run(System.Security.SecurityContext,System.Threading.ContextCallback,System.Object)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-284">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-284">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlow?displayProperty=nameWithType> | <span data-ttu-id="bb99c-285">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-285">All</span></span> |
| <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity?displayProperty=nameWithType> | <span data-ttu-id="bb99c-286">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-286">All</span></span> |

## <a name="systemsecurityclaims"></a><span data-ttu-id="bb99c-287">System.Security.Claims</span><span class="sxs-lookup"><span data-stu-id="bb99c-287">System.Security.Claims</span></span>

| <span data-ttu-id="bb99c-288">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-288">Member</span></span> | <span data-ttu-id="bb99c-289">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-289">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Claims.ClaimsPrincipal.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-290">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-290">All</span></span> |
| <xref:System.Security.Claims.ClaimsPrincipal.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-291">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-291">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo)> | <span data-ttu-id="bb99c-292">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-292">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-293">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-293">All</span></span> |
| <xref:System.Security.Claims.ClaimsIdentity.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-294">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-294">All</span></span> |

## <a name="systemsecuritycryptography"></a><span data-ttu-id="bb99c-295">System.Security.Cryptography</span><span class="sxs-lookup"><span data-stu-id="bb99c-295">System.Security.Cryptography</span></span>

| <span data-ttu-id="bb99c-296">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-296">Member</span></span> | <span data-ttu-id="bb99c-297">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-297">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-298">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-298">All</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.%23ctor%2A> | <span data-ttu-id="bb99c-299">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-299">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Accessible?displayProperty=nameWithType> | <span data-ttu-id="bb99c-300">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-300">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Exportable?displayProperty=nameWithType> | <span data-ttu-id="bb99c-301">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-301">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.HardwareDevice?displayProperty=nameWithType> | <span data-ttu-id="bb99c-302">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-302">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="bb99c-303">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-303">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.KeyNumber?displayProperty=nameWithType> | <span data-ttu-id="bb99c-304">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-304">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.MachineKeyStore?displayProperty=nameWithType> | <span data-ttu-id="bb99c-305">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-305">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Protected?displayProperty=nameWithType> | <span data-ttu-id="bb99c-306">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-306">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderName?displayProperty=nameWithType> | <span data-ttu-id="bb99c-307">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-307">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.ProviderType?displayProperty=nameWithType> | <span data-ttu-id="bb99c-308">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-308">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.RandomlyGenerated?displayProperty=nameWithType> | <span data-ttu-id="bb99c-309">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-309">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.Removable?displayProperty=nameWithType> | <span data-ttu-id="bb99c-310">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-310">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.CspKeyContainerInfo.UniqueKeyContainerName?displayProperty=nameWithType> | <span data-ttu-id="bb99c-311">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-311">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.HashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="bb99c-312">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-312">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create?displayProperty=nameWithType> | <span data-ttu-id="bb99c-313">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-313">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-314">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-314">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashCore%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-315">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-315">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.HashFinal%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-316">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-316">All</span></span> |
| <xref:System.Security.Cryptography.HMAC.Initialize%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-317">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-317">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="bb99c-318">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-318">All</span></span> |
| <xref:System.Security.Cryptography.KeyedHashAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-319">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-319">All</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Protect%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-320">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-320">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.ProtectedData.Unprotect%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-321">Linux e macOS</span><span class="sxs-lookup"><span data-stu-id="bb99c-321">Linux and macOS</span></span> |
| <xref:System.Security.Cryptography.RSA.FromXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-322">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-322">All</span></span> |
| <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-323">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-323">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create?displayProperty=nameWithType> | <span data-ttu-id="bb99c-324">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-324">All</span></span> |
| <xref:System.Security.Cryptography.SymmetricAlgorithm.Create(System.String)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-325">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-325">All</span></span> |

## <a name="systemsecuritycryptographypkcs"></a><span data-ttu-id="bb99c-326">System.Security.Cryptography.Pkcs</span><span class="sxs-lookup"><span data-stu-id="bb99c-326">System.Security.Cryptography.Pkcs</span></span>

| <span data-ttu-id="bb99c-327">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-327">Member</span></span> | <span data-ttu-id="bb99c-328">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-328">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.Pkcs.CmsSigner.%23ctor(System.Security.Cryptography.CspParameters)> | <span data-ttu-id="bb99c-329">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-329">All</span></span> |
| <xref:System.Security.Cryptography.Pkcs.SignerInfo.ComputeCounterSignature?displayProperty=nameWithType> | <span data-ttu-id="bb99c-330">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-330">All</span></span> |

## <a name="systemsecuritycryptographyx509certificates"></a><span data-ttu-id="bb99c-331">System.Security.Cryptography.X509Certificates</span><span class="sxs-lookup"><span data-stu-id="bb99c-331">System.Security.Cryptography.X509Certificates</span></span>

| <span data-ttu-id="bb99c-332">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-332">Member</span></span> | <span data-ttu-id="bb99c-333">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-333">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-334">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-334">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate.Import%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-335">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-335">All</span></span> |
| <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-336">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-336">All</span></span> |
| <span data-ttu-id="bb99c-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (definir somente)</span><span class="sxs-lookup"><span data-stu-id="bb99c-337"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> (set only)</span></span> | <span data-ttu-id="bb99c-338">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-338">All</span></span> |

## <a name="systemsecurityauthenticationextendedprotection"></a><span data-ttu-id="bb99c-339">System.Security.Authentication.ExtendedProtection</span><span class="sxs-lookup"><span data-stu-id="bb99c-339">System.Security.Authentication.ExtendedProtection</span></span>

| <span data-ttu-id="bb99c-340">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-340">Member</span></span> | <span data-ttu-id="bb99c-341">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-341">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-342">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-342">All</span></span> |

## <a name="systemsecuritypolicy"></a><span data-ttu-id="bb99c-343">System. Security. Policy</span><span class="sxs-lookup"><span data-stu-id="bb99c-343">System.Security.Policy</span></span>

| <span data-ttu-id="bb99c-344">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-344">Member</span></span> | <span data-ttu-id="bb99c-345">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-345">Platforms that throw</span></span> |
| - | - |
| <xref:System.Security.Policy.Hash.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-346">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-346">All</span></span> |

## <a name="systemserviceprocessservicecontroller"></a><span data-ttu-id="bb99c-347">System.ServiceProcess.ServiceController</span><span class="sxs-lookup"><span data-stu-id="bb99c-347">System.ServiceProcess.ServiceController</span></span>

| <span data-ttu-id="bb99c-348">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-348">Member</span></span> | <span data-ttu-id="bb99c-349">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-349">Platforms that throw</span></span> |
| - | - |
| <xref:System.ServiceProcess.TimeoutException.%23ctor(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)> | <span data-ttu-id="bb99c-350">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-350">All</span></span> |

## <a name="systemtextregularexpressions"></a><span data-ttu-id="bb99c-351">System.Text.RegularExpressions</span><span class="sxs-lookup"><span data-stu-id="bb99c-351">System.Text.RegularExpressions</span></span>

| <span data-ttu-id="bb99c-352">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-352">Member</span></span> | <span data-ttu-id="bb99c-353">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-353">Platforms that throw</span></span> |
| - | - |
| <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-354">Tudo</span><span class="sxs-lookup"><span data-stu-id="bb99c-354">All</span></span> |

## <a name="systemthreading"></a><span data-ttu-id="bb99c-355">System.Threading</span><span class="sxs-lookup"><span data-stu-id="bb99c-355">System.Threading</span></span>

| <span data-ttu-id="bb99c-356">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-356">Member</span></span> | <span data-ttu-id="bb99c-357">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-357">Platforms that throw</span></span> |
| - | - |
| <xref:System.Threading.CompressedStack.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-358">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-358">All</span></span> |
| <xref:System.Threading.ExecutionContext.GetObjectData(System.Runtime.Serialization.SerializationInfo,System.Runtime.Serialization.StreamingContext)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-359">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-359">All</span></span> |
| <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> | <span data-ttu-id="bb99c-360">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-360">All</span></span> |
| <xref:System.Threading.Thread.ResetAbort?displayProperty=nameWithType> | <span data-ttu-id="bb99c-361">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-361">All</span></span> |
| <xref:System.Threading.Thread.Resume?displayProperty=nameWithType> | <span data-ttu-id="bb99c-362">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-362">All</span></span> |
| <xref:System.Threading.Thread.Suspend?displayProperty=nameWithType> | <span data-ttu-id="bb99c-363">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-363">All</span></span> |

## <a name="systemxml"></a><span data-ttu-id="bb99c-364">System.Xml</span><span class="sxs-lookup"><span data-stu-id="bb99c-364">System.Xml</span></span>

| <span data-ttu-id="bb99c-365">Membro</span><span class="sxs-lookup"><span data-stu-id="bb99c-365">Member</span></span> | <span data-ttu-id="bb99c-366">Plataformas que lançam</span><span class="sxs-lookup"><span data-stu-id="bb99c-366">Platforms that throw</span></span> |
| - | - |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.Byte[],System.Int32,System.Int32,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-367">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-367">All</span></span> |
| <xref:System.Xml.XmlDictionaryReader.CreateMtomReader(System.IO.Stream,System.Text.Encoding[],System.String,System.Xml.XmlDictionaryReaderQuotas,System.Int32,System.Xml.OnXmlDictionaryReaderClose)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-368">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-368">All</span></span> |
| <xref:System.Xml.XmlDictionaryWriter.CreateMtomWriter(System.IO.Stream,System.Text.Encoding,System.Int32,System.String,System.String,System.String,System.Boolean,System.Boolean)?displayProperty=nameWithType> | <span data-ttu-id="bb99c-369">Todos</span><span class="sxs-lookup"><span data-stu-id="bb99c-369">All</span></span> |

## <a name="see-also"></a><span data-ttu-id="bb99c-370">Confira também</span><span class="sxs-lookup"><span data-stu-id="bb99c-370">See also</span></span>

- [<span data-ttu-id="bb99c-371">Alterações recentes de migração do .NET Framework para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb99c-371">Breaking changes for migration from .NET Framework to .NET Core</span></span>](fx-core.md)
- [<span data-ttu-id="bb99c-372">Serialização binária no .NET Core</span><span class="sxs-lookup"><span data-stu-id="bb99c-372">Binary serialization in .NET Core</span></span>](../../standard/serialization/binary-serialization.md#net-core)
- [<span data-ttu-id="bb99c-373">Analisador de portabilidade .NET</span><span class="sxs-lookup"><span data-stu-id="bb99c-373">.NET portability analyzer</span></span>](../../standard/analyzers/portability-analyzer.md)
