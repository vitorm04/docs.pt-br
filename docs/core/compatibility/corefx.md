---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 07/27/2020
ms.openlocfilehash: b86ceab784fd295acf500986f7e64731eb8ed0a3
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756099"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="6afb2-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="6afb2-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="6afb2-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6afb2-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="6afb2-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="6afb2-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="6afb2-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="6afb2-106">Breaking change</span></span> | <span data-ttu-id="6afb2-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="6afb2-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="6afb2-108">Ordem das marcas na atividade. as marcas são revertidas</span><span class="sxs-lookup"><span data-stu-id="6afb2-108">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="6afb2-109">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-109">5.0</span></span> |
| [<span data-ttu-id="6afb2-110">Nomes de parâmetros alterados no RC1</span><span class="sxs-lookup"><span data-stu-id="6afb2-110">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="6afb2-111">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-111">5.0</span></span> |
| [<span data-ttu-id="6afb2-112">Atributos OSPlatform renomeados ou removidos</span><span class="sxs-lookup"><span data-stu-id="6afb2-112">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="6afb2-113">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-113">5.0</span></span> |
| [<span data-ttu-id="6afb2-114">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="6afb2-114">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="6afb2-115">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-115">5.0</span></span> |
| [<span data-ttu-id="6afb2-116">Propriedades obsoletas em ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="6afb2-116">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="6afb2-117">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-117">5.0</span></span> |
| [<span data-ttu-id="6afb2-118">Verificações IsSupported de hardware intrínsecas podem diferir para tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="6afb2-118">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="6afb2-119">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-119">5.0</span></span> |
| [<span data-ttu-id="6afb2-120">Nomes de parâmetro alterados em assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="6afb2-120">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="6afb2-121">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-121">5.0</span></span> |
| [<span data-ttu-id="6afb2-122">Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX</span><span class="sxs-lookup"><span data-stu-id="6afb2-122">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="6afb2-123">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-123">5.0</span></span> |
| [<span data-ttu-id="6afb2-124">Reconhecimento de URI de caminhos UNC no UNIX</span><span class="sxs-lookup"><span data-stu-id="6afb2-124">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="6afb2-125">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-125">5.0</span></span> |
| [<span data-ttu-id="6afb2-126">Environment. OSVersion retorna a versão correta do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="6afb2-126">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="6afb2-127">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-127">5.0</span></span> |
| [<span data-ttu-id="6afb2-128">Complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou</span><span class="sxs-lookup"><span data-stu-id="6afb2-128">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="6afb2-129">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-129">5.0</span></span> |
| [<span data-ttu-id="6afb2-130">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="6afb2-130">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="6afb2-131">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-131">5.0</span></span> |
| [<span data-ttu-id="6afb2-132">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="6afb2-132">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="6afb2-133">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-133">5.0</span></span> |
| [<span data-ttu-id="6afb2-134">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6afb2-134">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="6afb2-135">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-135">5.0</span></span> |
| [<span data-ttu-id="6afb2-136">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="6afb2-136">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="6afb2-137">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-137">5.0</span></span> |
| [<span data-ttu-id="6afb2-138">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="6afb2-138">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="6afb2-139">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-139">5.0</span></span> |
| [<span data-ttu-id="6afb2-140">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="6afb2-140">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="6afb2-141">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-141">5.0</span></span> |
| [<span data-ttu-id="6afb2-142">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="6afb2-142">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="6afb2-143">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-143">5.0</span></span> |
| [<span data-ttu-id="6afb2-144">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="6afb2-144">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="6afb2-145">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-145">5.0</span></span> |
| [<span data-ttu-id="6afb2-146">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="6afb2-146">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="6afb2-147">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-147">5.0</span></span> |
| [<span data-ttu-id="6afb2-148">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="6afb2-148">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="6afb2-149">5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-149">5.0</span></span> |
| [<span data-ttu-id="6afb2-150">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="6afb2-150">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="6afb2-151">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-151">3.0</span></span> |
| [<span data-ttu-id="6afb2-152">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="6afb2-152">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="6afb2-153">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-153">3.0</span></span> |
| [<span data-ttu-id="6afb2-154">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="6afb2-154">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="6afb2-155">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-155">3.0</span></span> |
| [<span data-ttu-id="6afb2-156">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="6afb2-156">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="6afb2-157">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-157">3.0</span></span> |
| [<span data-ttu-id="6afb2-158">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="6afb2-158">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="6afb2-159">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-159">3.0</span></span> |
| [<span data-ttu-id="6afb2-160">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="6afb2-160">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="6afb2-161">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-161">3.0</span></span> |
| [<span data-ttu-id="6afb2-162">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="6afb2-162">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="6afb2-163">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-163">3.0</span></span> |
| [<span data-ttu-id="6afb2-164">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="6afb2-164">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="6afb2-165">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-165">3.0</span></span> |
| [<span data-ttu-id="6afb2-166">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="6afb2-166">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="6afb2-167">3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-167">3.0</span></span> |
| [<span data-ttu-id="6afb2-168">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="6afb2-168">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="6afb2-169">2.1</span><span class="sxs-lookup"><span data-stu-id="6afb2-169">2.1</span></span> |
| [<span data-ttu-id="6afb2-170">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="6afb2-170">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="6afb2-171">2.1</span><span class="sxs-lookup"><span data-stu-id="6afb2-171">2.1</span></span> |
| [<span data-ttu-id="6afb2-172">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="6afb2-172">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="6afb2-173">2.1</span><span class="sxs-lookup"><span data-stu-id="6afb2-173">2.1</span></span> |
| [<span data-ttu-id="6afb2-174">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="6afb2-174">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="6afb2-175">1,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-175">1.0</span></span> |
| [<span data-ttu-id="6afb2-176">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="6afb2-176">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="6afb2-177">1,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-177">1.0</span></span> |
| [<span data-ttu-id="6afb2-178">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="6afb2-178">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="6afb2-179">1,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-179">1.0</span></span> |
| [<span data-ttu-id="6afb2-180">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="6afb2-180">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="6afb2-181">1,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-181">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="6afb2-182">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="6afb2-182">.NET 5.0</span></span>

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

***

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

## <a name="net-core-30"></a><span data-ttu-id="6afb2-183">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-183">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="6afb2-184">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="6afb2-184">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="6afb2-185">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="6afb2-185">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
