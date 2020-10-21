---
title: Recursos obsoletos no .NET 5 +
description: Saiba mais sobre as APIs que estão marcadas como obsoletas no .NET 5,0 e versões posteriores que produzem avisos do compilador SYSLIB.
ms.date: 10/20/2020
ms.openlocfilehash: 13f5fb10cfe693ed621b3f45fc22e024875890c8
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92333217"
---
# <a name="obsolete-features-in-net-5"></a><span data-ttu-id="ffe37-103">Recursos obsoletos no .NET 5</span><span class="sxs-lookup"><span data-stu-id="ffe37-103">Obsolete features in .NET 5</span></span>

<span data-ttu-id="ffe37-104">A partir do .NET 5,0, algumas APIs que são marcadas recentemente como obsoletas fazem uso de duas novas propriedades no <xref:System.ObsoleteAttribute> .</span><span class="sxs-lookup"><span data-stu-id="ffe37-104">Starting in .NET 5.0, some APIs that are newly marked as obsolete make use of two new properties on <xref:System.ObsoleteAttribute>.</span></span>

- <span data-ttu-id="ffe37-105">A <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> propriedade informa ao compilador para gerar avisos de compilação usando uma ID de diagnóstico Personalizada.</span><span class="sxs-lookup"><span data-stu-id="ffe37-105">The <xref:System.ObsoleteAttribute.DiagnosticId?displayProperty=nameWithType> property tells the compiler to generate build warnings using a custom diagnostic ID.</span></span> <span data-ttu-id="ffe37-106">A ID personalizada permite que o aviso obsoletion seja suprimido especificamente e separadamente um do outro.</span><span class="sxs-lookup"><span data-stu-id="ffe37-106">The custom ID allows for obsoletion warning to be suppressed specifically and separately from one another.</span></span> <span data-ttu-id="ffe37-107">No caso do .NET 5 + obsoletions, o formato da ID de diagnóstico personalizado é `SYSLIBxxxx` .</span><span class="sxs-lookup"><span data-stu-id="ffe37-107">In the case of the .NET 5+ obsoletions, the format for the custom diagnostic ID is `SYSLIBxxxx`.</span></span>

- <span data-ttu-id="ffe37-108">A <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> propriedade informa ao compilador para incluir um link de URL para saber mais sobre o obsoletion.</span><span class="sxs-lookup"><span data-stu-id="ffe37-108">The <xref:System.ObsoleteAttribute.UrlFormat?displayProperty=nameWithType> property tells the compiler to include a URL link to learn more about the obsoletion.</span></span>

<span data-ttu-id="ffe37-109">Se você encontrar avisos de compilação ou erros devido ao uso de uma API obsoleta, siga as diretrizes específicas fornecidas para a ID de diagnóstico listada na seção de [referência](#reference) .</span><span class="sxs-lookup"><span data-stu-id="ffe37-109">If you encounter build warnings or errors due to usage of an obsolete API, follow the specific guidance provided for the diagnostic ID listed in the [Reference](#reference) section.</span></span> <span data-ttu-id="ffe37-110">Avisos ou erros para essas obsoletions *não podem* ser suprimidos usando a [CS0618 (ID de diagnóstico padrão)](../../csharp/language-reference/compiler-messages/cs0618.md) para tipos ou membros obsoletos; `SYSLIBxxxx` em vez disso, use os valores de ID de diagnóstico personalizados.</span><span class="sxs-lookup"><span data-stu-id="ffe37-110">Warnings or errors for these obsoletions *can't* be suppressed using the [standard diagnostic ID (CS0618)](../../csharp/language-reference/compiler-messages/cs0618.md) for obsolete types or members; use the custom `SYSLIBxxxx` diagnostic ID values instead.</span></span> <span data-ttu-id="ffe37-111">Para obter mais informações, consulte [suprimir avisos](#suppress-warnings).</span><span class="sxs-lookup"><span data-stu-id="ffe37-111">For more information, see [Suppress warnings](#suppress-warnings).</span></span>

## <a name="reference"></a><span data-ttu-id="ffe37-112">Referência</span><span class="sxs-lookup"><span data-stu-id="ffe37-112">Reference</span></span>

<span data-ttu-id="ffe37-113">A tabela a seguir fornece um índice para o `SYSLIBxxxx` obsoletions no .NET 5 +.</span><span class="sxs-lookup"><span data-stu-id="ffe37-113">The following table provides an index to the `SYSLIBxxxx` obsoletions in .NET 5+.</span></span>

| <span data-ttu-id="ffe37-114">ID do diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ffe37-114">Diagnostic ID</span></span> | <span data-ttu-id="ffe37-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffe37-115">Description</span></span> |
| - | - |
| [<span data-ttu-id="ffe37-116">SYSLIB0001</span><span class="sxs-lookup"><span data-stu-id="ffe37-116">SYSLIB0001</span></span>](syslib0001.md) | <span data-ttu-id="ffe37-117">A codificação UTF-7 é insegura e não deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="ffe37-117">The UTF-7 encoding is insecure and should not be used.</span></span> <span data-ttu-id="ffe37-118">Considere usar UTF-8 em vez disso.</span><span class="sxs-lookup"><span data-stu-id="ffe37-118">Consider using UTF-8 instead.</span></span> |
| [<span data-ttu-id="ffe37-119">SYSLIB0002</span><span class="sxs-lookup"><span data-stu-id="ffe37-119">SYSLIB0002</span></span>](syslib0002.md) | <span data-ttu-id="ffe37-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Não é respeitado pelo tempo de execução e não deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="ffe37-120"><xref:System.Security.Permissions.PrincipalPermissionAttribute> is not honored by the runtime and must not be used.</span></span> |
| [<span data-ttu-id="ffe37-121">SYSLIB0003</span><span class="sxs-lookup"><span data-stu-id="ffe37-121">SYSLIB0003</span></span>](syslib0003.md) | <span data-ttu-id="ffe37-122">A CAS (segurança de acesso ao código) não tem suporte nem é respeitada pelo tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffe37-122">Code access security (CAS) is not supported or honored by the runtime.</span></span> |
| [<span data-ttu-id="ffe37-123">SYSLIB0004</span><span class="sxs-lookup"><span data-stu-id="ffe37-123">SYSLIB0004</span></span>](syslib0004.md) | <span data-ttu-id="ffe37-124">Não há suporte para o recurso CER (região de execução restrita).</span><span class="sxs-lookup"><span data-stu-id="ffe37-124">The constrained execution region (CER) feature is not supported.</span></span> |
| [<span data-ttu-id="ffe37-125">SYSLIB0005</span><span class="sxs-lookup"><span data-stu-id="ffe37-125">SYSLIB0005</span></span>](syslib0005.md) | <span data-ttu-id="ffe37-126">Não há suporte para o GAC (cache de assembly global).</span><span class="sxs-lookup"><span data-stu-id="ffe37-126">The global assembly cache (GAC) is not supported.</span></span> |
| [<span data-ttu-id="ffe37-127">SYSLIB0006</span><span class="sxs-lookup"><span data-stu-id="ffe37-127">SYSLIB0006</span></span>](syslib0006.md) | <span data-ttu-id="ffe37-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> Não é suportado e gera <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="ffe37-128"><xref:System.Threading.Thread.Abort?displayProperty=nameWithType> is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="ffe37-129">SYSLIB0007</span><span class="sxs-lookup"><span data-stu-id="ffe37-129">SYSLIB0007</span></span>](syslib0007.md) | <span data-ttu-id="ffe37-130">Não há suporte para a implementação padrão desse algoritmo de criptografia.</span><span class="sxs-lookup"><span data-stu-id="ffe37-130">The default implementation of this cryptography algorithm is not supported.</span></span> |
| [<span data-ttu-id="ffe37-131">SYSLIB0008</span><span class="sxs-lookup"><span data-stu-id="ffe37-131">SYSLIB0008</span></span>](syslib0008.md) | <span data-ttu-id="ffe37-132">A <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API não é suportada e gera <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="ffe37-132">The <xref:System.Runtime.CompilerServices.DebugInfoGenerator.CreatePdbGenerator> API is not supported and throws <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="ffe37-133">SYSLIB0009</span><span class="sxs-lookup"><span data-stu-id="ffe37-133">SYSLIB0009</span></span>](syslib0009.md) | <span data-ttu-id="ffe37-134">Os <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> métodos e não têm suporte e geram <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="ffe37-134">The <xref:System.Net.AuthenticationManager.Authenticate%2A?displayProperty=nameWithType> and <xref:System.Net.AuthenticationManager.PreAuthenticate%2A?displayProperty=nameWithType> methods are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="ffe37-135">SYSLIB0010</span><span class="sxs-lookup"><span data-stu-id="ffe37-135">SYSLIB0010</span></span>](syslib0010.md) | <span data-ttu-id="ffe37-136">Algumas APIs de comunicação remota não têm suporte e geram <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="ffe37-136">Some remoting APIs are not supported and throw <xref:System.PlatformNotSupportedException>.</span></span> |
| [<span data-ttu-id="ffe37-137">SYSLIB0011</span><span class="sxs-lookup"><span data-stu-id="ffe37-137">SYSLIB0011</span></span>](syslib0011.md) | <span data-ttu-id="ffe37-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a serialização está obsoleta e não deve ser usada.</span><span class="sxs-lookup"><span data-stu-id="ffe37-138"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is obsolete and should not be used.</span></span> |
| [<span data-ttu-id="ffe37-139">SYSLIB0012</span><span class="sxs-lookup"><span data-stu-id="ffe37-139">SYSLIB0012</span></span>](syslib0012.md) | <span data-ttu-id="ffe37-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> e <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> são incluídos apenas para .NET Framework compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="ffe37-140"><xref:System.Reflection.Assembly.CodeBase?displayProperty=nameWithType> and <xref:System.Reflection.Assembly.EscapedCodeBase?displayProperty=nameWithType> are only included for .NET Framework compatibility.</span></span> <span data-ttu-id="ffe37-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> em seu lugar.</span><span class="sxs-lookup"><span data-stu-id="ffe37-141">Use <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> instead.</span></span> |

## <a name="suppress-warnings"></a><span data-ttu-id="ffe37-142">Suprimir avisos</span><span class="sxs-lookup"><span data-stu-id="ffe37-142">Suppress warnings</span></span>

<span data-ttu-id="ffe37-143">Se você precisar usar as APIs obsoletas e o diagnóstico não for exibido `SYSLIBxxxx` como um erro, poderá suprimir o aviso no código ou no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="ffe37-143">If you must use the obsolete APIs and the `SYSLIBxxxx` diagnostic does not surface as an error, you can suppress the warning in code or in your project file.</span></span>

<span data-ttu-id="ffe37-144">No código:</span><span class="sxs-lookup"><span data-stu-id="ffe37-144">In code:</span></span>

```csharp
// Disable the warning.
#pragma warning disable SYSLIB0001
// Code that uses obsolete API.
...
// Re-enable the warning.
#pragma warning restore SYSLIB0001
```

<span data-ttu-id="ffe37-145">Arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="ffe37-145">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
   <TargetFramework>net5.0</TargetFramework>
   <!-- NoWarn below suppresses SYSLIB0001 project-wide -->
   <NoWarn>$(NoWarn);SYSLIB0001</NoWarn>
  </PropertyGroup>
</Project>
```

> [!NOTE]
> <span data-ttu-id="ffe37-146">Suprimir um aviso dessa forma apenas desabilita esse aviso obsoletion específico.</span><span class="sxs-lookup"><span data-stu-id="ffe37-146">Suppressing a warning in this way only disables that specific obsoletion warning.</span></span> <span data-ttu-id="ffe37-147">Ele não desabilita nenhum outro aviso, incluindo outros avisos de obsoletion.</span><span class="sxs-lookup"><span data-stu-id="ffe37-147">It doesn't disable any other warnings, including other obsoletion warnings.</span></span>
