---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 07/27/2020
ms.openlocfilehash: c3207ac7630d794f77c793cc6d1d52e158c0c084
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738809"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="39ab5-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="39ab5-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="39ab5-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="39ab5-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="39ab5-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="39ab5-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="39ab5-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="39ab5-106">Breaking change</span></span> | <span data-ttu-id="39ab5-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="39ab5-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="39ab5-108">Nomes de parâmetros alterados no RC1</span><span class="sxs-lookup"><span data-stu-id="39ab5-108">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="39ab5-109">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-109">5.0</span></span> |
| [<span data-ttu-id="39ab5-110">Atributos OSPlatform renomeados ou removidos</span><span class="sxs-lookup"><span data-stu-id="39ab5-110">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="39ab5-111">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-111">5.0</span></span> |
| [<span data-ttu-id="39ab5-112">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="39ab5-112">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="39ab5-113">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-113">5.0</span></span> |
| [<span data-ttu-id="39ab5-114">Propriedades obsoletas em ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="39ab5-114">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="39ab5-115">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-115">5.0</span></span> |
| [<span data-ttu-id="39ab5-116">Verificações IsSupported de hardware intrínsecas podem diferir para tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="39ab5-116">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="39ab5-117">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-117">5.0</span></span> |
| [<span data-ttu-id="39ab5-118">Nomes de parâmetro alterados em assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="39ab5-118">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="39ab5-119">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-119">5.0</span></span> |
| [<span data-ttu-id="39ab5-120">Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX</span><span class="sxs-lookup"><span data-stu-id="39ab5-120">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="39ab5-121">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-121">5.0</span></span> |
| [<span data-ttu-id="39ab5-122">Reconhecimento de URI de caminhos UNC no UNIX</span><span class="sxs-lookup"><span data-stu-id="39ab5-122">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="39ab5-123">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-123">5.0</span></span> |
| [<span data-ttu-id="39ab5-124">Environment. OSVersion retorna a versão correta do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="39ab5-124">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="39ab5-125">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-125">5.0</span></span> |
| [<span data-ttu-id="39ab5-126">Complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou</span><span class="sxs-lookup"><span data-stu-id="39ab5-126">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="39ab5-127">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-127">5.0</span></span> |
| [<span data-ttu-id="39ab5-128">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="39ab5-128">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="39ab5-129">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-129">5.0</span></span> |
| [<span data-ttu-id="39ab5-130">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="39ab5-130">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="39ab5-131">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-131">5.0</span></span> |
| [<span data-ttu-id="39ab5-132">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39ab5-132">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="39ab5-133">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-133">5.0</span></span> |
| [<span data-ttu-id="39ab5-134">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="39ab5-134">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="39ab5-135">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-135">5.0</span></span> |
| [<span data-ttu-id="39ab5-136">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="39ab5-136">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="39ab5-137">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-137">5.0</span></span> |
| [<span data-ttu-id="39ab5-138">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="39ab5-138">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="39ab5-139">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-139">5.0</span></span> |
| [<span data-ttu-id="39ab5-140">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="39ab5-140">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="39ab5-141">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-141">5.0</span></span> |
| [<span data-ttu-id="39ab5-142">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="39ab5-142">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="39ab5-143">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-143">5.0</span></span> |
| [<span data-ttu-id="39ab5-144">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="39ab5-144">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="39ab5-145">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-145">5.0</span></span> |
| [<span data-ttu-id="39ab5-146">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="39ab5-146">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="39ab5-147">5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-147">5.0</span></span> |
| [<span data-ttu-id="39ab5-148">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="39ab5-148">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="39ab5-149">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-149">3.0</span></span> |
| [<span data-ttu-id="39ab5-150">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="39ab5-150">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="39ab5-151">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-151">3.0</span></span> |
| [<span data-ttu-id="39ab5-152">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="39ab5-152">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="39ab5-153">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-153">3.0</span></span> |
| [<span data-ttu-id="39ab5-154">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="39ab5-154">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="39ab5-155">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-155">3.0</span></span> |
| [<span data-ttu-id="39ab5-156">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="39ab5-156">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="39ab5-157">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-157">3.0</span></span> |
| [<span data-ttu-id="39ab5-158">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="39ab5-158">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="39ab5-159">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-159">3.0</span></span> |
| [<span data-ttu-id="39ab5-160">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="39ab5-160">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="39ab5-161">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-161">3.0</span></span> |
| [<span data-ttu-id="39ab5-162">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="39ab5-162">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="39ab5-163">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-163">3.0</span></span> |
| [<span data-ttu-id="39ab5-164">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="39ab5-164">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="39ab5-165">3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-165">3.0</span></span> |
| [<span data-ttu-id="39ab5-166">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="39ab5-166">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="39ab5-167">2.1</span><span class="sxs-lookup"><span data-stu-id="39ab5-167">2.1</span></span> |
| [<span data-ttu-id="39ab5-168">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="39ab5-168">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="39ab5-169">2.1</span><span class="sxs-lookup"><span data-stu-id="39ab5-169">2.1</span></span> |
| [<span data-ttu-id="39ab5-170">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="39ab5-170">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="39ab5-171">2.1</span><span class="sxs-lookup"><span data-stu-id="39ab5-171">2.1</span></span> |
| [<span data-ttu-id="39ab5-172">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="39ab5-172">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="39ab5-173">1,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-173">1.0</span></span> |
| [<span data-ttu-id="39ab5-174">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="39ab5-174">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="39ab5-175">1,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-175">1.0</span></span> |
| [<span data-ttu-id="39ab5-176">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="39ab5-176">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="39ab5-177">1,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-177">1.0</span></span> |
| [<span data-ttu-id="39ab5-178">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="39ab5-178">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="39ab5-179">1,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-179">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="39ab5-180">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="39ab5-180">.NET 5.0</span></span>

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

***

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

***

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

***

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

***

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

***

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

***

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

***

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

***

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

***

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

***

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="39ab5-181">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-181">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="39ab5-182">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="39ab5-182">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="39ab5-183">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="39ab5-183">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
