---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 07/27/2020
ms.openlocfilehash: 8ea1cd995484c2930c8a9c2eb4c7419be57cf9c0
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440165"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="ded40-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="ded40-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="ded40-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ded40-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="ded40-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="ded40-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="ded40-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="ded40-106">Breaking change</span></span> | <span data-ttu-id="ded40-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ded40-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="ded40-108">LastIndexOf aprimorou o tratamento de cadeias de caracteres de pesquisa vazias</span><span class="sxs-lookup"><span data-stu-id="ded40-108">LastIndexOf has improved handling of empty search strings</span></span>](#lastindexof-has-improved-handling-of-empty-search-strings) | <span data-ttu-id="ded40-109">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-109">5.0</span></span> |
| [<span data-ttu-id="ded40-110">As APIs do cache de assembly global estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="ded40-110">Global assembly cache APIs are obsolete</span></span>](#global-assembly-cache-apis-are-obsolete) | <span data-ttu-id="ded40-111">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-111">5.0</span></span> |
| [<span data-ttu-id="ded40-112">As APIs de comunicação remota estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="ded40-112">Remoting APIs are obsolete</span></span>](#remoting-apis-are-obsolete) | <span data-ttu-id="ded40-113">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-113">5.0</span></span> |
| [<span data-ttu-id="ded40-114">A maioria das APIs de segurança de acesso a código está obsoleta</span><span class="sxs-lookup"><span data-stu-id="ded40-114">Most code access security APIs are obsolete</span></span>](#most-code-access-security-apis-are-obsolete) | <span data-ttu-id="ded40-115">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-115">5.0</span></span> |
| [<span data-ttu-id="ded40-116">API obsoletions com IDs de diagnóstico não padrão</span><span class="sxs-lookup"><span data-stu-id="ded40-116">API obsoletions with non-default diagnostic IDs</span></span>](#api-obsoletions-with-non-default-diagnostic-ids) | <span data-ttu-id="ded40-117">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-117">5.0</span></span> |
| [<span data-ttu-id="ded40-118">O valor de FrameworkDescription é .NET, em vez de .NET Core</span><span class="sxs-lookup"><span data-stu-id="ded40-118">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="ded40-119">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-119">5.0</span></span> |
| [<span data-ttu-id="ded40-120">Alterações de comportamento da API relacionadas ao assembly para o formato de publicação de arquivo único</span><span class="sxs-lookup"><span data-stu-id="ded40-120">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="ded40-121">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-121">5.0</span></span> |
| [<span data-ttu-id="ded40-122">Ordem das marcas na atividade. as marcas são revertidas</span><span class="sxs-lookup"><span data-stu-id="ded40-122">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="ded40-123">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-123">5.0</span></span> |
| [<span data-ttu-id="ded40-124">Nomes de parâmetros alterados no RC1</span><span class="sxs-lookup"><span data-stu-id="ded40-124">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="ded40-125">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-125">5.0</span></span> |
| [<span data-ttu-id="ded40-126">Atributos OSPlatform renomeados ou removidos</span><span class="sxs-lookup"><span data-stu-id="ded40-126">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="ded40-127">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-127">5.0</span></span> |
| [<span data-ttu-id="ded40-128">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="ded40-128">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="ded40-129">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-129">5.0</span></span> |
| [<span data-ttu-id="ded40-130">Propriedades obsoletas em ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="ded40-130">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="ded40-131">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-131">5.0</span></span> |
| [<span data-ttu-id="ded40-132">Verificações IsSupported de hardware intrínsecas podem diferir para tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="ded40-132">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="ded40-133">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-133">5.0</span></span> |
| [<span data-ttu-id="ded40-134">Nomes de parâmetro alterados em assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="ded40-134">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="ded40-135">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-135">5.0</span></span> |
| [<span data-ttu-id="ded40-136">Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX</span><span class="sxs-lookup"><span data-stu-id="ded40-136">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="ded40-137">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-137">5.0</span></span> |
| [<span data-ttu-id="ded40-138">Reconhecimento de URI de caminhos UNC no UNIX</span><span class="sxs-lookup"><span data-stu-id="ded40-138">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="ded40-139">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-139">5.0</span></span> |
| [<span data-ttu-id="ded40-140">Environment. OSVersion retorna a versão correta do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="ded40-140">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="ded40-141">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-141">5.0</span></span> |
| [<span data-ttu-id="ded40-142">Complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou</span><span class="sxs-lookup"><span data-stu-id="ded40-142">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="ded40-143">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-143">5.0</span></span> |
| [<span data-ttu-id="ded40-144">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="ded40-144">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="ded40-145">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-145">5.0</span></span> |
| [<span data-ttu-id="ded40-146">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="ded40-146">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="ded40-147">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-147">5.0</span></span> |
| [<span data-ttu-id="ded40-148">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ded40-148">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="ded40-149">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-149">5.0</span></span> |
| [<span data-ttu-id="ded40-150">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="ded40-150">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="ded40-151">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-151">5.0</span></span> |
| [<span data-ttu-id="ded40-152">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="ded40-152">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="ded40-153">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-153">5.0</span></span> |
| [<span data-ttu-id="ded40-154">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="ded40-154">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="ded40-155">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-155">5.0</span></span> |
| [<span data-ttu-id="ded40-156">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="ded40-156">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="ded40-157">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-157">5.0</span></span> |
| [<span data-ttu-id="ded40-158">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="ded40-158">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="ded40-159">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-159">5.0</span></span> |
| [<span data-ttu-id="ded40-160">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="ded40-160">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="ded40-161">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-161">5.0</span></span> |
| [<span data-ttu-id="ded40-162">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="ded40-162">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="ded40-163">5.0</span><span class="sxs-lookup"><span data-stu-id="ded40-163">5.0</span></span> |
| [<span data-ttu-id="ded40-164">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="ded40-164">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="ded40-165">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-165">3.0</span></span> |
| [<span data-ttu-id="ded40-166">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="ded40-166">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="ded40-167">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-167">3.0</span></span> |
| [<span data-ttu-id="ded40-168">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="ded40-168">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="ded40-169">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-169">3.0</span></span> |
| [<span data-ttu-id="ded40-170">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="ded40-170">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="ded40-171">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-171">3.0</span></span> |
| [<span data-ttu-id="ded40-172">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="ded40-172">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="ded40-173">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-173">3.0</span></span> |
| [<span data-ttu-id="ded40-174">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="ded40-174">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="ded40-175">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-175">3.0</span></span> |
| [<span data-ttu-id="ded40-176">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="ded40-176">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="ded40-177">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-177">3.0</span></span> |
| [<span data-ttu-id="ded40-178">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="ded40-178">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="ded40-179">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-179">3.0</span></span> |
| [<span data-ttu-id="ded40-180">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="ded40-180">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="ded40-181">3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-181">3.0</span></span> |
| [<span data-ttu-id="ded40-182">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="ded40-182">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="ded40-183">2.1</span><span class="sxs-lookup"><span data-stu-id="ded40-183">2.1</span></span> |
| [<span data-ttu-id="ded40-184">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="ded40-184">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="ded40-185">2.1</span><span class="sxs-lookup"><span data-stu-id="ded40-185">2.1</span></span> |
| [<span data-ttu-id="ded40-186">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="ded40-186">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="ded40-187">2.1</span><span class="sxs-lookup"><span data-stu-id="ded40-187">2.1</span></span> |
| [<span data-ttu-id="ded40-188">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="ded40-188">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="ded40-189">1.0</span><span class="sxs-lookup"><span data-stu-id="ded40-189">1.0</span></span> |
| [<span data-ttu-id="ded40-190">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="ded40-190">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="ded40-191">1.0</span><span class="sxs-lookup"><span data-stu-id="ded40-191">1.0</span></span> |
| [<span data-ttu-id="ded40-192">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="ded40-192">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="ded40-193">1.0</span><span class="sxs-lookup"><span data-stu-id="ded40-193">1.0</span></span> |
| [<span data-ttu-id="ded40-194">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="ded40-194">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="ded40-195">1.0</span><span class="sxs-lookup"><span data-stu-id="ded40-195">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="ded40-196">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="ded40-196">.NET 5.0</span></span>

[!INCLUDE [lastindexof-improved-handling-of-empty-values](../../../includes/core-changes/corefx/5.0/lastindexof-improved-handling-of-empty-values.md)]

***

[!INCLUDE [remoting-apis-obsolete](../../../includes/core-changes/corefx/5.0/remoting-apis-obsolete.md)]

<span data-ttu-id="ded40-197">\*\*_</span><span class="sxs-lookup"><span data-stu-id="ded40-197">\*\*_</span></span>

[!INCLUDE [globalassemblycache-property-obsolete](../../../includes/core-changes/corefx/5.0/global-assembly-cache-apis-obsolete.md)]

_*_

[!INCLUDE [code-access-security-apis-obsolete](../../../includes/core-changes/corefx/5.0/code-access-security-apis-obsolete.md)]

_*_

[!INCLUDE [obsolete-apis-with-custom-diagnostics](../../../includes/core-changes/corefx/5.0/obsolete-apis-with-custom-diagnostics.md)]

_*_

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

_*_

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

_*_

[!INCLUDE [reverse-order-of-tags-in-activity-property](../../../includes/core-changes/corefx/5.0/reverse-order-of-tags-in-activity-property.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names-rc1](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names-rc1.md)]

_*_

[!INCLUDE [os-platform-attributes-renamed](../../../includes/core-changes/corefx/5.0/os-platform-attributes-renamed.md)]

_*_

[!INCLUDE [thread-abort-obsolete](../../../includes/core-changes/corefx/5.0/thread-abort-obsolete.md)]

_*_

[!INCLUDE [obsolete-consoleloggeroptions-properties](../../../includes/core-changes/corefx/5.0/obsolete-consoleloggeroptions-properties.md)]

_*_

[!INCLUDE [hardware-instrinsics-issupported-checks](../../../includes/core-changes/corefx/5.0/hardware-instrinsics-issupported-checks.md)]

_*_

[!INCLUDE [reference-assembly-parameter-names](../../../includes/core-changes/corefx/5.0/reference-assembly-parameter-names.md)]

_*_

[!INCLUDE [non-ascii-chars-in-uri-parsed-correctly](../../../includes/core-changes/corefx/5.0/non-ascii-chars-in-uri-parsed-correctly.md)]

_*_

[!INCLUDE [unc-path-recognition-unix](../../../includes/core-changes/corefx/5.0/unc-path-recognition-unix.md)]

_*_

[!INCLUDE [environment-osversion-returns-correct-version](../../../includes/core-changes/corefx/5.0/environment-osversion-returns-correct-version.md)]

_*_

[!INCLUDE [orderby-firstordefault-complexity-increase](../../../includes/core-changes/corefx/5.0/orderby-firstordefault-complexity-increase.md)]

_*_

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

_*_

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

_*_

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

_*_

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

_*_

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

_*_

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

_*_

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

_*_

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

_*_

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

_*_

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="ded40-198">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="ded40-198">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

_*_

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

_*_

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

_*_

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

_*_

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

_*_

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

_*_

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

_*_

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

_*_

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

_*_

## <a name="net-core-21"></a><span data-ttu-id="ded40-199">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="ded40-199">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="ded40-200">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="ded40-200">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="ded40-201">_\*\*</span><span class="sxs-lookup"><span data-stu-id="ded40-201">_\*\*</span></span>
