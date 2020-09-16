---
ms.openlocfilehash: e3c9f23ca73ed9b85d09680ec15251ebe02c7f8e
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065124"
---
### <a name="ca1416-platform-compatibility"></a><span data-ttu-id="c12b8-101">CA1416: compatibilidade de plataforma</span><span class="sxs-lookup"><span data-stu-id="c12b8-101">CA1416: Platform compatibility</span></span>

<span data-ttu-id="c12b8-102">A regra do analisador de código .NET CA1416 está habilitada, por padrão, a partir do .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="c12b8-102">.NET code analyzer rule CA1416 is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="c12b8-103">Ele produz um aviso de compilação para chamadas a APIs específicas da plataforma de sites de chamada que não verificam o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="c12b8-103">It produces a build warning for calls to platform-specific APIs from call sites that don't verify the operating system.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c12b8-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="c12b8-104">Change description</span></span>

<span data-ttu-id="c12b8-105">A partir do .NET 5,0, o SDK do .NET inclui [analisadores de código-fonte .net](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="c12b8-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="c12b8-106">Várias dessas regras estão habilitadas, por padrão, incluindo CA1416.</span><span class="sxs-lookup"><span data-stu-id="c12b8-106">Several of these rules are enabled, by default, including CA1416.</span></span> <span data-ttu-id="c12b8-107">Se o seu projeto contiver código que viole essa regra e estiver configurado para tratar avisos como erros, essa alteração poderá interromper sua compilação.</span><span class="sxs-lookup"><span data-stu-id="c12b8-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span> <span data-ttu-id="c12b8-108">A regra CA1416 informa quando você está usando APIs específicas da plataforma de locais onde o contexto da plataforma não é verificado.</span><span class="sxs-lookup"><span data-stu-id="c12b8-108">Rule CA1416 informs you when you're using platform-specific APIs from places where the platform context isn't verified.</span></span>

<span data-ttu-id="c12b8-109">A regra CA1416, o analisador de compatibilidade de plataforma, trabalha em conjunto com alguns outros recursos que são novos no .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="c12b8-109">Rule CA1416, the platform compatibility analyzer, works hand-in-hand with some other features that are new in .NET 5.0.</span></span> <span data-ttu-id="c12b8-110">O .NET 5,0 `SupportedOSPlatformAttribute` apresenta `UnsupportedOSPlatformAttribute` atributos e (chamados <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> e <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> em uma versão prévia anterior), que permitem especificar as plataformas em que uma API *tem* ou *não* tem suporte.</span><span class="sxs-lookup"><span data-stu-id="c12b8-110">.NET 5.0 introduces `SupportedOSPlatformAttribute` and `UnsupportedOSPlatformAttribute` attributes (named <xref:System.Runtime.Versioning.MinimumOSPlatformAttribute> and <xref:System.Runtime.Versioning.RemovedInOSPlatformAttribute> in an earlier preview release), which let you specify the platforms that an API *is* or *isn't* supported on.</span></span> <span data-ttu-id="c12b8-111">Na ausência desses atributos, pressupõe-se que uma API tenha suporte em todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="c12b8-111">In the absence of these attributes, an API is assumed to be supported on all platforms.</span></span> <span data-ttu-id="c12b8-112">Esses atributos foram aplicados a APIs específicas da plataforma nas principais bibliotecas do .NET.</span><span class="sxs-lookup"><span data-stu-id="c12b8-112">These attributes have been applied to platform-specific APIs in the core .NET libraries.</span></span>

<span data-ttu-id="c12b8-113">Em projetos que visam plataformas para as quais as APIs que eles usam não estão disponíveis, a regra CA1416 sinaliza qualquer chamada de API específica da plataforma onde o contexto da plataforma não é verificado.</span><span class="sxs-lookup"><span data-stu-id="c12b8-113">In projects that target platforms for which APIs that they use aren't available, rule CA1416 flags any platform-specific API call where the platform context isn't verified.</span></span> <span data-ttu-id="c12b8-114">A maioria das APIs que agora estão decoradas com `SupportedOSPlatformAttribute` os `UnsupportedOSPlatformAttribute` atributos e gera <xref:System.PlatformNotSupportedException> exceções quando elas são invocadas em um sistema operacional sem suporte.</span><span class="sxs-lookup"><span data-stu-id="c12b8-114">Most of the APIs that are now decorated with the `SupportedOSPlatformAttribute` and `UnsupportedOSPlatformAttribute` attributes throw <xref:System.PlatformNotSupportedException> exceptions when they're invoked on an unsupported operating system.</span></span> <span data-ttu-id="c12b8-115">Agora que essas APIs estão marcadas como específicas da plataforma, a regra CA1416 ajuda você a evitar exceções em tempo de execução <xref:System.PlatformNotSupportedException> adicionando verificações do sistema operacional aos seus sites de chamada.</span><span class="sxs-lookup"><span data-stu-id="c12b8-115">Now that these APIs are marked as platform-specific, rule CA1416 helps you prevent run-time <xref:System.PlatformNotSupportedException> exceptions by adding OS checks to your call sites.</span></span>

#### <a name="examples"></a><span data-ttu-id="c12b8-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c12b8-116">Examples</span></span>

- <span data-ttu-id="c12b8-117"><xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType>Só há suporte para o método no Windows (ele é decorado com `[SupportedOSPlatform("windows")]` ).</span><span class="sxs-lookup"><span data-stu-id="c12b8-117">The <xref:System.Console.Beep(System.Int32,System.Int32)?displayProperty=nameWithType> method is only supported on Windows (it's decorated with `[SupportedOSPlatform("windows")]`).</span></span> <span data-ttu-id="c12b8-118">O código a seguir produzirá um aviso de CA1416 no momento da compilação se o projeto tiver como [destino](../../../../docs/standard/frameworks.md) `net5.0` (mas não `net5.0-windows` ).</span><span class="sxs-lookup"><span data-stu-id="c12b8-118">The following code will produce a CA1416 warning at build time if the project [targets](../../../../docs/standard/frameworks.md) `net5.0` (but not `net5.0-windows`).</span></span> <span data-ttu-id="c12b8-119">Para ações que você pode executar para evitar o aviso, consulte a [ação recomendada](#recommended-action).</span><span class="sxs-lookup"><span data-stu-id="c12b8-119">For actions you can take to avoid the warning, see [Recommended action](#recommended-action).</span></span>

  ```csharp
  public void PlayCMajor()
  {
      Console.Beep(261, 1000);
  }
  ```

- <span data-ttu-id="c12b8-120"><xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType>Não há suporte para o método no navegador (ele está decorado com `[UnsupportedOSPlatform("browser")]` ).</span><span class="sxs-lookup"><span data-stu-id="c12b8-120">The <xref:System.Drawing.Image.FromFile(System.String)?displayProperty=nameWithType> method is not supported in the browser (it's decorated with `[UnsupportedOSPlatform("browser")]`).</span></span> <span data-ttu-id="c12b8-121">O código a seguir produzirá um aviso de CA1416 no momento da compilação se o projeto usar o SDK do Webassembly mais elaborado ( `<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">` ) ou incluir `browser` como uma plataforma com suporte ( `<SupportedPlatform Include="browser" />` ) no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c12b8-121">The following code will produce a CA1416 warning at build time if the project uses the Blazor WebAssembly SDK (`<Project Sdk="Microsoft.NET.Sdk.BlazorWebAssembly">`) or includes `browser` as a supported platform (`<SupportedPlatform Include="browser" />`) in the project file.</span></span>

  ```csharp
  public void CreateImage()
  {
      Image newImage = Image.FromFile("SampImag.jpg");
  }
  ```

#### <a name="version-introduced"></a><span data-ttu-id="c12b8-122">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="c12b8-122">Version introduced</span></span>

<span data-ttu-id="c12b8-123">RC1 5,0</span><span class="sxs-lookup"><span data-stu-id="c12b8-123">5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c12b8-124">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="c12b8-124">Recommended action</span></span>

<span data-ttu-id="c12b8-125">Verifique se as APIs específicas da plataforma são chamadas apenas quando o código está sendo executado em uma plataforma apropriada.</span><span class="sxs-lookup"><span data-stu-id="c12b8-125">Ensure that platform-specific APIs are only called when the code is running on an appropriate platform.</span></span> <span data-ttu-id="c12b8-126">Você pode verificar o sistema operacional atual usando um dos `Is<Platform>` métodos na classe, <xref:System.OperatingSystem?displayProperty=nameWithType> por exemplo,, `System.OperatingSystem.IsWindows()` antes de chamar uma API específica da plataforma.</span><span class="sxs-lookup"><span data-stu-id="c12b8-126">You can check the current operating system using one of the `Is<Platform>` methods in the <xref:System.OperatingSystem?displayProperty=nameWithType> class, for example, `System.OperatingSystem.IsWindows()`, before calling a platform-specific API.</span></span>

<span data-ttu-id="c12b8-127">Você pode usar um dos `Is<Platform>` métodos na condição de uma `if` instrução:</span><span class="sxs-lookup"><span data-stu-id="c12b8-127">You can use one of the `Is<Platform>` methods in the condition of an `if` statement:</span></span>

```csharp
public void PlayCMajor()
{
    if (OperatingSystem.IsWindows())
    {
        Console.Beep(261, 1000);
    }
}
```

<span data-ttu-id="c12b8-128">Ou, se você não quiser a sobrecarga de uma `if` instrução adicional em tempo de execução, chame <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="c12b8-128">Or, if you don't want the overhead of an additional `if` statement at run time, call <xref:System.Diagnostics.Debug.Assert(System.Boolean)?displayProperty=nameWithType> instead:</span></span>

```csharp
public void PlayCMajor()
{
    Debug.Assert(OperatingSystem.IsWindows());
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="c12b8-129">Você também pode marcar sua API como específica da plataforma, caso em que a carga dos requisitos de verificação cai em seus chamadores.</span><span class="sxs-lookup"><span data-stu-id="c12b8-129">You can also mark your API as platform-specific, in which case the burden of checking requirements falls on your callers.</span></span> <span data-ttu-id="c12b8-130">Você pode marcar métodos ou tipos específicos ou um assembly inteiro.</span><span class="sxs-lookup"><span data-stu-id="c12b8-130">You can mark specific methods or types or an entire assembly.</span></span>

```csharp
[SupportedOSPlatform("windows")]
public void PlayCMajor()
{
    Console.Beep(261, 1000);
}
```

<span data-ttu-id="c12b8-131">Se você não quiser corrigir todos os seus sites de chamada, poderá escolher uma das seguintes opções para suprimir o aviso:</span><span class="sxs-lookup"><span data-stu-id="c12b8-131">If you don't want to fix all your call sites, you can choose one of the following options to suppress the warning:</span></span>

- <span data-ttu-id="c12b8-132">Para suprimir a regra CA1416, você pode fazer isso usando `#pragma` o ou o sinalizador do compilador [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) ou [definindo a severidade da regra](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) como `none` em um arquivo. editorconfig.</span><span class="sxs-lookup"><span data-stu-id="c12b8-132">To suppress rule CA1416, you can do so using `#pragma` or the [-nowarn](../../../../docs/csharp/language-reference/compiler-options/nowarn-compiler-option.md) compiler flag, or by [setting the rule's severity](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md#suppress-violations) to `none` in an .editorconfig file.</span></span>

  ```csharp
  public void PlayCMajor()
  {
  #pragma warning disable CA1416
      Console.Beep(261, 1000);
  #pragma warning restore CA1416
  }
  ```

- <span data-ttu-id="c12b8-133">Para desabilitar completamente a análise de código, defina `EnableNETAnalyzers` como `false` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="c12b8-133">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="c12b8-134">Para obter mais informações, consulte [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="c12b8-134">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="c12b8-135">Categoria</span><span class="sxs-lookup"><span data-stu-id="c12b8-135">Category</span></span>

- <span data-ttu-id="c12b8-136">Análise de código</span><span class="sxs-lookup"><span data-stu-id="c12b8-136">Code analysis</span></span>
- <span data-ttu-id="c12b8-137">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="c12b8-137">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c12b8-138">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="c12b8-138">Affected APIs</span></span>

<span data-ttu-id="c12b8-139">Para a plataforma Windows:</span><span class="sxs-lookup"><span data-stu-id="c12b8-139">For Windows platform:</span></span>

- <span data-ttu-id="c12b8-140">Todas as APIs listadas em <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md> .</span><span class="sxs-lookup"><span data-stu-id="c12b8-140">All APIs listed at <https://github.com/dotnet/designs/blob/master/accepted/2020/windows-specific-apis/windows-specific-apis.md>.</span></span>
- <xref:System.Security.Cryptography.DSAOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDiffieHellmanOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.ECDsaOpenSsl?displayProperty=fullName>
- <xref:System.Security.Cryptography.RSAOpenSsl?displayProperty=fullName>

<span data-ttu-id="c12b8-141">Para a plataforma Webassembly mais incrivelmente:</span><span class="sxs-lookup"><span data-stu-id="c12b8-141">For Blazor WebAssembly platform:</span></span>

- <span data-ttu-id="c12b8-142">Todas as APIs listadas em <https://github.com/dotnet/runtime/issues/41087> .</span><span class="sxs-lookup"><span data-stu-id="c12b8-142">All APIs listed at <https://github.com/dotnet/runtime/issues/41087>.</span></span>

<!--

#### Affected APIs

- ``

-->

#### <a name="see-also"></a><span data-ttu-id="c12b8-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="c12b8-143">See also</span></span>

- [<span data-ttu-id="c12b8-144">Analisador de API do .NET</span><span class="sxs-lookup"><span data-stu-id="c12b8-144">.NET API analyzer</span></span>](../../../../docs/standard/analyzers/api-analyzer.md)
