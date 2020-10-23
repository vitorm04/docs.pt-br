---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 07/27/2020
ms.openlocfilehash: 900fd4e0e071f19aa286dec84632006870822f26
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434902"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="923b0-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="923b0-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="923b0-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="923b0-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="923b0-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="923b0-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="923b0-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="923b0-106">Breaking change</span></span> | <span data-ttu-id="923b0-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="923b0-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="923b0-108">As APIs do cache de assembly global estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="923b0-108">Global assembly cache APIs are obsolete</span></span>](#global-assembly-cache-apis-are-obsolete) | <span data-ttu-id="923b0-109">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-109">5.0</span></span> |
| [<span data-ttu-id="923b0-110">As APIs de comunicação remota estão obsoletas</span><span class="sxs-lookup"><span data-stu-id="923b0-110">Remoting APIs are obsolete</span></span>](#remoting-apis-are-obsolete) | <span data-ttu-id="923b0-111">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-111">5.0</span></span> |
| [<span data-ttu-id="923b0-112">A maioria das APIs de segurança de acesso a código está obsoleta</span><span class="sxs-lookup"><span data-stu-id="923b0-112">Most code access security APIs are obsolete</span></span>](#most-code-access-security-apis-are-obsolete) | <span data-ttu-id="923b0-113">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-113">5.0</span></span> |
| [<span data-ttu-id="923b0-114">API obsoletions com IDs de diagnóstico não padrão</span><span class="sxs-lookup"><span data-stu-id="923b0-114">API obsoletions with non-default diagnostic IDs</span></span>](#api-obsoletions-with-non-default-diagnostic-ids) | <span data-ttu-id="923b0-115">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-115">5.0</span></span> |
| [<span data-ttu-id="923b0-116">O valor de FrameworkDescription é .NET, em vez de .NET Core</span><span class="sxs-lookup"><span data-stu-id="923b0-116">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="923b0-117">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-117">5.0</span></span> |
| [<span data-ttu-id="923b0-118">Alterações de comportamento da API relacionadas ao assembly para o formato de publicação de arquivo único</span><span class="sxs-lookup"><span data-stu-id="923b0-118">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="923b0-119">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-119">5.0</span></span> |
| [<span data-ttu-id="923b0-120">Ordem das marcas na atividade. as marcas são revertidas</span><span class="sxs-lookup"><span data-stu-id="923b0-120">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="923b0-121">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-121">5.0</span></span> |
| [<span data-ttu-id="923b0-122">Nomes de parâmetros alterados no RC1</span><span class="sxs-lookup"><span data-stu-id="923b0-122">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="923b0-123">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-123">5.0</span></span> |
| [<span data-ttu-id="923b0-124">Atributos OSPlatform renomeados ou removidos</span><span class="sxs-lookup"><span data-stu-id="923b0-124">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="923b0-125">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-125">5.0</span></span> |
| [<span data-ttu-id="923b0-126">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="923b0-126">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="923b0-127">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-127">5.0</span></span> |
| [<span data-ttu-id="923b0-128">Propriedades obsoletas em ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="923b0-128">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="923b0-129">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-129">5.0</span></span> |
| [<span data-ttu-id="923b0-130">Verificações IsSupported de hardware intrínsecas podem diferir para tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="923b0-130">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="923b0-131">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-131">5.0</span></span> |
| [<span data-ttu-id="923b0-132">Nomes de parâmetro alterados em assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="923b0-132">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="923b0-133">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-133">5.0</span></span> |
| [<span data-ttu-id="923b0-134">Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX</span><span class="sxs-lookup"><span data-stu-id="923b0-134">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="923b0-135">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-135">5.0</span></span> |
| [<span data-ttu-id="923b0-136">Reconhecimento de URI de caminhos UNC no UNIX</span><span class="sxs-lookup"><span data-stu-id="923b0-136">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="923b0-137">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-137">5.0</span></span> |
| [<span data-ttu-id="923b0-138">Environment. OSVersion retorna a versão correta do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="923b0-138">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="923b0-139">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-139">5.0</span></span> |
| [<span data-ttu-id="923b0-140">Complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou</span><span class="sxs-lookup"><span data-stu-id="923b0-140">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="923b0-141">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-141">5.0</span></span> |
| [<span data-ttu-id="923b0-142">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="923b0-142">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="923b0-143">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-143">5.0</span></span> |
| [<span data-ttu-id="923b0-144">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="923b0-144">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="923b0-145">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-145">5.0</span></span> |
| [<span data-ttu-id="923b0-146">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="923b0-146">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="923b0-147">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-147">5.0</span></span> |
| [<span data-ttu-id="923b0-148">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="923b0-148">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="923b0-149">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-149">5.0</span></span> |
| [<span data-ttu-id="923b0-150">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="923b0-150">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="923b0-151">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-151">5.0</span></span> |
| [<span data-ttu-id="923b0-152">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="923b0-152">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="923b0-153">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-153">5.0</span></span> |
| [<span data-ttu-id="923b0-154">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="923b0-154">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="923b0-155">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-155">5.0</span></span> |
| [<span data-ttu-id="923b0-156">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="923b0-156">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="923b0-157">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-157">5.0</span></span> |
| [<span data-ttu-id="923b0-158">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="923b0-158">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="923b0-159">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-159">5.0</span></span> |
| [<span data-ttu-id="923b0-160">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="923b0-160">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="923b0-161">5.0</span><span class="sxs-lookup"><span data-stu-id="923b0-161">5.0</span></span> |
| [<span data-ttu-id="923b0-162">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="923b0-162">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="923b0-163">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-163">3.0</span></span> |
| [<span data-ttu-id="923b0-164">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="923b0-164">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="923b0-165">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-165">3.0</span></span> |
| [<span data-ttu-id="923b0-166">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="923b0-166">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="923b0-167">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-167">3.0</span></span> |
| [<span data-ttu-id="923b0-168">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="923b0-168">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="923b0-169">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-169">3.0</span></span> |
| [<span data-ttu-id="923b0-170">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="923b0-170">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="923b0-171">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-171">3.0</span></span> |
| [<span data-ttu-id="923b0-172">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="923b0-172">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="923b0-173">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-173">3.0</span></span> |
| [<span data-ttu-id="923b0-174">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="923b0-174">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="923b0-175">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-175">3.0</span></span> |
| [<span data-ttu-id="923b0-176">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="923b0-176">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="923b0-177">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-177">3.0</span></span> |
| [<span data-ttu-id="923b0-178">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="923b0-178">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="923b0-179">3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-179">3.0</span></span> |
| [<span data-ttu-id="923b0-180">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="923b0-180">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="923b0-181">2.1</span><span class="sxs-lookup"><span data-stu-id="923b0-181">2.1</span></span> |
| [<span data-ttu-id="923b0-182">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="923b0-182">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="923b0-183">2.1</span><span class="sxs-lookup"><span data-stu-id="923b0-183">2.1</span></span> |
| [<span data-ttu-id="923b0-184">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="923b0-184">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="923b0-185">2.1</span><span class="sxs-lookup"><span data-stu-id="923b0-185">2.1</span></span> |
| [<span data-ttu-id="923b0-186">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="923b0-186">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="923b0-187">1.0</span><span class="sxs-lookup"><span data-stu-id="923b0-187">1.0</span></span> |
| [<span data-ttu-id="923b0-188">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="923b0-188">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="923b0-189">1.0</span><span class="sxs-lookup"><span data-stu-id="923b0-189">1.0</span></span> |
| [<span data-ttu-id="923b0-190">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="923b0-190">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="923b0-191">1.0</span><span class="sxs-lookup"><span data-stu-id="923b0-191">1.0</span></span> |
| [<span data-ttu-id="923b0-192">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="923b0-192">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="923b0-193">1.0</span><span class="sxs-lookup"><span data-stu-id="923b0-193">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="923b0-194">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="923b0-194">.NET 5.0</span></span>

[!INCLUDE [remoting-apis-obsolete](../../../includes/core-changes/corefx/5.0/remoting-apis-obsolete.md)]

***

[!INCLUDE [globalassemblycache-property-obsolete](../../../includes/core-changes/corefx/5.0/global-assembly-cache-apis-obsolete.md)]

<span data-ttu-id="923b0-195">\*\*_</span><span class="sxs-lookup"><span data-stu-id="923b0-195">\*\*_</span></span>

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

## <a name="net-core-30"></a><span data-ttu-id="923b0-196">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="923b0-196">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="923b0-197">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="923b0-197">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

_*_

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

_*_

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

_*_

## <a name="net-core-10"></a><span data-ttu-id="923b0-198">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="923b0-198">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

_*_

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

_*_

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

_*_

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

<span data-ttu-id="923b0-199">_\*\*</span><span class="sxs-lookup"><span data-stu-id="923b0-199">_\*\*</span></span>
