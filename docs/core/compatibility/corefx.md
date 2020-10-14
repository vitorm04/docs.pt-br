---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 07/27/2020
ms.openlocfilehash: 3ecf0e81a3adef097aafb760dc44498d7263f0b6
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050553"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="93711-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="93711-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="93711-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="93711-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="93711-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="93711-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="93711-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="93711-106">Breaking change</span></span> | <span data-ttu-id="93711-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="93711-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="93711-108">O valor de FrameworkDescription é .NET, em vez de .NET Core</span><span class="sxs-lookup"><span data-stu-id="93711-108">FrameworkDescription's value is .NET instead of .NET Core</span></span>](#frameworkdescriptions-value-is-net-instead-of-net-core) | <span data-ttu-id="93711-109">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-109">5.0</span></span> |
| [<span data-ttu-id="93711-110">Alterações de comportamento da API relacionadas ao assembly para o formato de publicação de arquivo único</span><span class="sxs-lookup"><span data-stu-id="93711-110">Assembly-related API behavior changes for single-file publishing format</span></span>](#assembly-related-api-behavior-changes-for-single-file-publishing-format) | <span data-ttu-id="93711-111">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-111">5.0</span></span> |
| [<span data-ttu-id="93711-112">Ordem das marcas na atividade. as marcas são revertidas</span><span class="sxs-lookup"><span data-stu-id="93711-112">Order of tags in Activity.Tags is reversed</span></span>](#order-of-tags-in-activitytags-is-reversed) | <span data-ttu-id="93711-113">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-113">5.0</span></span> |
| [<span data-ttu-id="93711-114">Nomes de parâmetros alterados no RC1</span><span class="sxs-lookup"><span data-stu-id="93711-114">Parameter names changed in RC1</span></span>](#parameter-names-changed-in-rc1) | <span data-ttu-id="93711-115">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-115">5.0</span></span> |
| [<span data-ttu-id="93711-116">Atributos OSPlatform renomeados ou removidos</span><span class="sxs-lookup"><span data-stu-id="93711-116">OSPlatform attributes renamed or removed</span></span>](#osplatform-attributes-renamed-or-removed) | <span data-ttu-id="93711-117">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-117">5.0</span></span> |
| [<span data-ttu-id="93711-118">Thread. Abort é obsoleto</span><span class="sxs-lookup"><span data-stu-id="93711-118">Thread.Abort is obsolete</span></span>](#threadabort-is-obsolete) | <span data-ttu-id="93711-119">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-119">5.0</span></span> |
| [<span data-ttu-id="93711-120">Propriedades obsoletas em ConsoleLoggerOptions</span><span class="sxs-lookup"><span data-stu-id="93711-120">Obsolete properties on ConsoleLoggerOptions</span></span>](#obsolete-properties-on-consoleloggeroptions) | <span data-ttu-id="93711-121">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-121">5.0</span></span> |
| [<span data-ttu-id="93711-122">Verificações IsSupported de hardware intrínsecas podem diferir para tipos aninhados</span><span class="sxs-lookup"><span data-stu-id="93711-122">Hardware intrinsic IsSupported checks may differ for nested types</span></span>](#hardware-intrinsic-issupported-checks-may-differ-for-nested-types) | <span data-ttu-id="93711-123">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-123">5.0</span></span> |
| [<span data-ttu-id="93711-124">Nomes de parâmetro alterados em assemblies de referência</span><span class="sxs-lookup"><span data-stu-id="93711-124">Parameter names changed in reference assemblies</span></span>](#parameter-names-changed-in-reference-assemblies) | <span data-ttu-id="93711-125">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-125">5.0</span></span> |
| [<span data-ttu-id="93711-126">Caminhos de URI com caracteres não ASCII são analisados corretamente no UNIX</span><span class="sxs-lookup"><span data-stu-id="93711-126">URI paths with non-ASCII characters parse correctly on Unix</span></span>](#uri-paths-with-non-ascii-characters-parse-correctly-on-unix) | <span data-ttu-id="93711-127">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-127">5.0</span></span> |
| [<span data-ttu-id="93711-128">Reconhecimento de URI de caminhos UNC no UNIX</span><span class="sxs-lookup"><span data-stu-id="93711-128">Uri recognition of UNC paths on Unix</span></span>](#uri-recognition-of-unc-paths-on-unix) | <span data-ttu-id="93711-129">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-129">5.0</span></span> |
| [<span data-ttu-id="93711-130">Environment. OSVersion retorna a versão correta do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="93711-130">Environment.OSVersion returns the correct operating system version</span></span>](#environmentosversion-returns-the-correct-operating-system-version) | <span data-ttu-id="93711-131">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-131">5.0</span></span> |
| [<span data-ttu-id="93711-132">Complexidade do LINQ OrderBy. primeiro {OrDefault} aumentou</span><span class="sxs-lookup"><span data-stu-id="93711-132">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>](#complexity-of-linq-orderbyfirstordefault-increased) | <span data-ttu-id="93711-133">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-133">5.0</span></span> |
| [<span data-ttu-id="93711-134">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="93711-134">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="93711-135">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-135">5.0</span></span> |
| [<span data-ttu-id="93711-136">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="93711-136">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="93711-137">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-137">5.0</span></span> |
| [<span data-ttu-id="93711-138">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="93711-138">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="93711-139">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-139">5.0</span></span> |
| [<span data-ttu-id="93711-140">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="93711-140">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="93711-141">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-141">5.0</span></span> |
| [<span data-ttu-id="93711-142">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="93711-142">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="93711-143">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-143">5.0</span></span> |
| [<span data-ttu-id="93711-144">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="93711-144">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="93711-145">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-145">5.0</span></span> |
| [<span data-ttu-id="93711-146">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="93711-146">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="93711-147">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-147">5.0</span></span> |
| [<span data-ttu-id="93711-148">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="93711-148">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="93711-149">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-149">5.0</span></span> |
| [<span data-ttu-id="93711-150">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="93711-150">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="93711-151">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-151">5.0</span></span> |
| [<span data-ttu-id="93711-152">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="93711-152">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="93711-153">5.0</span><span class="sxs-lookup"><span data-stu-id="93711-153">5.0</span></span> |
| [<span data-ttu-id="93711-154">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="93711-154">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="93711-155">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-155">3.0</span></span> |
| [<span data-ttu-id="93711-156">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="93711-156">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="93711-157">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-157">3.0</span></span> |
| [<span data-ttu-id="93711-158">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="93711-158">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="93711-159">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-159">3.0</span></span> |
| [<span data-ttu-id="93711-160">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="93711-160">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="93711-161">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-161">3.0</span></span> |
| [<span data-ttu-id="93711-162">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="93711-162">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="93711-163">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-163">3.0</span></span> |
| [<span data-ttu-id="93711-164">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="93711-164">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="93711-165">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-165">3.0</span></span> |
| [<span data-ttu-id="93711-166">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="93711-166">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="93711-167">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-167">3.0</span></span> |
| [<span data-ttu-id="93711-168">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="93711-168">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="93711-169">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-169">3.0</span></span> |
| [<span data-ttu-id="93711-170">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="93711-170">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="93711-171">3.0</span><span class="sxs-lookup"><span data-stu-id="93711-171">3.0</span></span> |
| [<span data-ttu-id="93711-172">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="93711-172">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="93711-173">2.1</span><span class="sxs-lookup"><span data-stu-id="93711-173">2.1</span></span> |
| [<span data-ttu-id="93711-174">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="93711-174">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="93711-175">2.1</span><span class="sxs-lookup"><span data-stu-id="93711-175">2.1</span></span> |
| [<span data-ttu-id="93711-176">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="93711-176">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="93711-177">2.1</span><span class="sxs-lookup"><span data-stu-id="93711-177">2.1</span></span> |
| [<span data-ttu-id="93711-178">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="93711-178">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="93711-179">1.0</span><span class="sxs-lookup"><span data-stu-id="93711-179">1.0</span></span> |
| [<span data-ttu-id="93711-180">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="93711-180">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="93711-181">1.0</span><span class="sxs-lookup"><span data-stu-id="93711-181">1.0</span></span> |
| [<span data-ttu-id="93711-182">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="93711-182">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="93711-183">1.0</span><span class="sxs-lookup"><span data-stu-id="93711-183">1.0</span></span> |
| [<span data-ttu-id="93711-184">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="93711-184">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="93711-185">1.0</span><span class="sxs-lookup"><span data-stu-id="93711-185">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="93711-186">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="93711-186">.NET 5.0</span></span>

[!INCLUDE [frameworkdescription-returns-net-not-net-core](../../../includes/core-changes/corefx/5.0/frameworkdescription-returns-net-not-net-core.md)]

***

[!INCLUDE [assembly-api-behavior-changes-for-single-file-publish](../../../includes/core-changes/corefx/5.0/assembly-api-behavior-changes-for-single-file-publish.md)]

***

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

## <a name="net-core-30"></a><span data-ttu-id="93711-187">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="93711-187">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="93711-188">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="93711-188">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="93711-189">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="93711-189">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
