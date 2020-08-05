---
ms.openlocfilehash: 1cb6e953aa57c72ee6a2665c521bada10e0786cf
ms.sourcegitcommit: 7499bdb428d63ed0e19e97f54d3d576c41598659
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/31/2020
ms.locfileid: "87455779"
---
### <a name="utf-7-code-paths-are-obsolete"></a><span data-ttu-id="82c37-101">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="82c37-101">UTF-7 code paths are obsolete</span></span>

<span data-ttu-id="82c37-102">A codificação UTF-7 não está mais em uso amplo entre aplicativos, e muitas especificações agora [proíbem seu uso](https://security.stackexchange.com/a/68609/3573) no intercâmbio.</span><span class="sxs-lookup"><span data-stu-id="82c37-102">The UTF-7 encoding is no longer in wide use among applications, and many specs now [forbid its use](https://security.stackexchange.com/a/68609/3573) in interchange.</span></span> <span data-ttu-id="82c37-103">Ele também é [usado ocasionalmente como um vetor de ataque](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) em aplicativos que não antecipam a ocorrência de dados codificados em UTF-7.</span><span class="sxs-lookup"><span data-stu-id="82c37-103">It's also occasionally [used as an attack vector](https://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=utf-7) in applications that don't anticipate encountering UTF-7-encoded data.</span></span> <span data-ttu-id="82c37-104">A Microsoft avisa sobre o uso do <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> porque não fornece detecção de erros.</span><span class="sxs-lookup"><span data-stu-id="82c37-104">Microsoft warns against use of <xref:System.Text.UTF7Encoding?displayProperty=nameWithType> because it doesn't provide error detection.</span></span>

<span data-ttu-id="82c37-105">Consequentemente, a <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriedade e os <xref:System.Text.UTF7Encoding.%23ctor%2A> construtores agora são obsoletos.</span><span class="sxs-lookup"><span data-stu-id="82c37-105">Consequently, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are now obsolete.</span></span> <span data-ttu-id="82c37-106">Além disso, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> e <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> não permite mais que você especifique `UTF-7` .</span><span class="sxs-lookup"><span data-stu-id="82c37-106">Additionally, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> and <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=nameWithType> no longer allow you to specify `UTF-7`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="82c37-107">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="82c37-107">Change description</span></span>

<span data-ttu-id="82c37-108">Anteriormente, você poderia criar uma instância da codificação UTF-7 usando as <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span><span class="sxs-lookup"><span data-stu-id="82c37-108">Previously, you could create an instance of the UTF-7 encoding by using the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> APIs.</span></span> <span data-ttu-id="82c37-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="82c37-109">For example:</span></span>

```csharp
Encoding enc1 = Encoding.GetEncoding("utf-7"); // By name.
Encoding enc2 = Encoding.GetEncoding(65000); // By code page.
```

<span data-ttu-id="82c37-110">Além disso, uma instância que representa a codificação UTF-7 foi enumerada pelo <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> método, que enumera todas as <xref:System.Text.Encoding> instâncias registradas no sistema.</span><span class="sxs-lookup"><span data-stu-id="82c37-110">Additionally, an instance that represents the UTF-7 encoding was enumerated by the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method, which enumerates all the <xref:System.Text.Encoding> instances registered on the system.</span></span>

<span data-ttu-id="82c37-111">A partir do .NET 5,0, a <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> propriedade e os <xref:System.Text.UTF7Encoding.%23ctor%2A> construtores são obsoletos e produzem um aviso `SYSLIB0001` (ou `MSLIB0001` em versões de visualização).</span><span class="sxs-lookup"><span data-stu-id="82c37-111">Starting in .NET 5.0, the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> property and <xref:System.Text.UTF7Encoding.%23ctor%2A> constructors are obsolete and produce warning `SYSLIB0001` (or `MSLIB0001` in preview versions).</span></span> <span data-ttu-id="82c37-112">No entanto, para reduzir o número de avisos que os chamadores recebem ao usar a <xref:System.Text.UTF7Encoding> classe, o <xref:System.Text.UTF7Encoding> tipo em si não é marcado como obsoleto.</span><span class="sxs-lookup"><span data-stu-id="82c37-112">However, to reduce the number of warnings that callers receive when using the <xref:System.Text.UTF7Encoding> class, the <xref:System.Text.UTF7Encoding> type itself is not marked obsolete.</span></span>

```csharp
// The next line generates warning SYSLIB0001.
UTF7Encoding enc = new UTF7Encoding();
// The next line does not generate a warning.
byte[] bytes = enc.GetBytes("Hello world!");
```

<span data-ttu-id="82c37-113">Além disso, os <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> métodos tratam o nome de codificação `utf-7` e a página de código `65000` como `unknown` .</span><span class="sxs-lookup"><span data-stu-id="82c37-113">Additionally, the <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> methods treat the encoding name `utf-7` and the code page `65000` as `unknown`.</span></span> <span data-ttu-id="82c37-114">Tratar a codificação como `unknown` faz com que o método gere um <xref:System.ArgumentException> .</span><span class="sxs-lookup"><span data-stu-id="82c37-114">Treating the encoding as `unknown` causes the method to throw an <xref:System.ArgumentException>.</span></span>

```csharp
// Throws ArgumentException, same as calling Encoding.GetEncoding("unknown").
Encoding enc = Encoding.GetEncoding("utf-7");
```

<span data-ttu-id="82c37-115">Por fim, o <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> método não inclui a codificação UTF-7 na <xref:System.Text.EncodingInfo> matriz que ela retorna.</span><span class="sxs-lookup"><span data-stu-id="82c37-115">Finally, the <xref:System.Text.Encoding.GetEncodings?displayProperty=nameWithType> method doesn't include the UTF-7 encoding in the <xref:System.Text.EncodingInfo> array that it returns.</span></span> <span data-ttu-id="82c37-116">A codificação é excluída porque não pode ser instanciada.</span><span class="sxs-lookup"><span data-stu-id="82c37-116">The encoding is excluded because it cannot be instantiated.</span></span>

```csharp
foreach (EncodingInfo encInfo in Encoding.GetEncodings())
{
    // The next line would throw if GetEncodings included UTF-7.
    Encoding enc = Encoding.GetEncoding(encInfo.Name);
}
```

#### <a name="reason-for-change"></a><span data-ttu-id="82c37-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="82c37-117">Reason for change</span></span>

<span data-ttu-id="82c37-118">Muitos aplicativos chamam `Encoding.GetEncoding("encoding-name")` um valor de nome de codificação fornecido por uma fonte não confiável.</span><span class="sxs-lookup"><span data-stu-id="82c37-118">Many applications call `Encoding.GetEncoding("encoding-name")` with an encoding name value that's provided by an untrusted source.</span></span> <span data-ttu-id="82c37-119">Por exemplo, um cliente ou servidor Web pode pegar a `charset` parte do `Content-Type` cabeçalho e passar o valor diretamente para `Encoding.GetEncoding` sem validá-lo.</span><span class="sxs-lookup"><span data-stu-id="82c37-119">For example, a web client or server might take the `charset` portion of the `Content-Type` header and pass the value directly to `Encoding.GetEncoding` without validating it.</span></span> <span data-ttu-id="82c37-120">Isso pode permitir que um ponto de extremidade mal-intencionado seja especificado `Content-Type: ...; charset=utf-7` , o que poderia causar um comportamento incorreto do aplicativo de recebimento.</span><span class="sxs-lookup"><span data-stu-id="82c37-120">This could allow a malicious endpoint to specify `Content-Type: ...; charset=utf-7`, which could cause the receiving application to misbehave.</span></span>

<span data-ttu-id="82c37-121">Além disso, a desabilitação de caminhos de código UTF-7 permite otimizar compiladores, como aqueles usados pelo mais alto, para remover totalmente esses caminhos de código do aplicativo resultante.</span><span class="sxs-lookup"><span data-stu-id="82c37-121">Additionally, disabling UTF-7 code paths allows optimizing compilers, such as those used by Blazor, to remove these code paths entirely from the resulting application.</span></span> <span data-ttu-id="82c37-122">Como resultado, os aplicativos compilados são executados com mais eficiência e ocupam menos espaço em disco.</span><span class="sxs-lookup"><span data-stu-id="82c37-122">As a result, the compiled applications run more efficiently and take less disk space.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="82c37-123">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="82c37-123">Version introduced</span></span>

<span data-ttu-id="82c37-124">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="82c37-124">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="82c37-125">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="82c37-125">Recommended action</span></span>

<span data-ttu-id="82c37-126">Na maioria dos casos, você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="82c37-126">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="82c37-127">No entanto, para aplicativos que já ativaram caminhos de código relacionados ao UTF-7, considere as diretrizes a seguir.</span><span class="sxs-lookup"><span data-stu-id="82c37-127">However, for apps that have previously activated UTF-7-related code paths, consider the guidance that follows.</span></span>

- <span data-ttu-id="82c37-128">Se seu aplicativo chama <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> nomes de codificação desconhecidos fornecidos por uma fonte não confiável:</span><span class="sxs-lookup"><span data-stu-id="82c37-128">If your app calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> with unknown encoding names provided by an untrusted source:</span></span>

  <span data-ttu-id="82c37-129">Em vez disso, compare os nomes de codificação com uma lista de permissão configurável.</span><span class="sxs-lookup"><span data-stu-id="82c37-129">Instead, compare the encoding names against a configurable allow list.</span></span> <span data-ttu-id="82c37-130">A lista de permissões configuráveis deve, no mínimo, incluir o "UTF-8" padrão do setor.</span><span class="sxs-lookup"><span data-stu-id="82c37-130">The configurable allow list should at minimum include the industry-standard "utf-8".</span></span> <span data-ttu-id="82c37-131">Dependendo de seus clientes e requisitos regulatórios, você também pode precisar permitir codificações específicas de região, como "GB18030".</span><span class="sxs-lookup"><span data-stu-id="82c37-131">Depending on your clients and regulatory requirements, you may also need to allow region-specific encodings, such as "GB18030".</span></span>

  <span data-ttu-id="82c37-132">Se você não implementar uma lista de permissões, o <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> retornará qualquer um <xref:System.Text.Encoding> que esteja embutido no sistema ou que seja registrado por meio de um personalizado <xref:System.Text.EncodingProvider> .</span><span class="sxs-lookup"><span data-stu-id="82c37-132">If you don't implement an allow list, <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> will return any <xref:System.Text.Encoding> that's built into the system or that's registered via a custom <xref:System.Text.EncodingProvider>.</span></span> <span data-ttu-id="82c37-133">Auditore os requisitos do serviço para validar que esse é o comportamento desejado.</span><span class="sxs-lookup"><span data-stu-id="82c37-133">Audit your service's requirements to validate that this is the desired behavior.</span></span> <span data-ttu-id="82c37-134">O UTF-7 continua desabilitado por padrão, a menos que o aplicativo habilite novamente a opção de compatibilidade mencionada posteriormente neste artigo.</span><span class="sxs-lookup"><span data-stu-id="82c37-134">UTF-7 continues to be disabled by default unless your application re-enables the compatibility switch mentioned later in this article.</span></span>

- <span data-ttu-id="82c37-135">Se você estiver usando <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> dentro de seu próprio protocolo ou formato de arquivo:</span><span class="sxs-lookup"><span data-stu-id="82c37-135">If you're using <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding> within your own protocol or file format:</span></span>

  <span data-ttu-id="82c37-136">Alterne para o usando o <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> ou o <xref:System.Text.UTF8Encoding> .</span><span class="sxs-lookup"><span data-stu-id="82c37-136">Switch to using <xref:System.Text.Encoding.UTF8?displayProperty=nameWithType> or <xref:System.Text.UTF8Encoding>.</span></span> <span data-ttu-id="82c37-137">O UTF-8 é um padrão da indústria e tem amplo suporte em linguagens, sistemas operacionais e tempos de execução.</span><span class="sxs-lookup"><span data-stu-id="82c37-137">UTF-8 is an industry standard and is widely supported across languages, operating systems, and runtimes.</span></span> <span data-ttu-id="82c37-138">O uso de UTF-8 facilita a manutenção futura de seu código e o torna mais interoperável com o restante do ecossistema.</span><span class="sxs-lookup"><span data-stu-id="82c37-138">Using UTF-8 eases future maintenance of your code and makes it more interoperable with the rest of the ecosystem.</span></span>

- <span data-ttu-id="82c37-139">Se você estiver comparando uma <xref:System.Text.Encoding> instância do <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="82c37-139">If you're comparing an <xref:System.Text.Encoding> instance against <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType>:</span></span>

  <span data-ttu-id="82c37-140">Em vez disso, considere executar uma verificação na página de código UTF-7 conhecida, que é `65000` .</span><span class="sxs-lookup"><span data-stu-id="82c37-140">Instead, consider performing a check against the well-known UTF-7 code page, which is `65000`.</span></span> <span data-ttu-id="82c37-141">Ao comparar com a página de código, você evita o aviso e também lida com alguns casos de borda, como se alguém chamou `new UTF7Encoding()` ou subclasse o tipo.</span><span class="sxs-lookup"><span data-stu-id="82c37-141">By comparing against the code page, you avoid the warning and also handle some edge cases, such as if somebody called `new UTF7Encoding()` or subclassed the type.</span></span>

  ```csharp
  void DoSomething(Encoding enc)
  {
      // Don't perform the check this way.
      // It produces a warning and misses some edge cases.
      if (enc == Encoding.UTF7)
      {
          // Encoding is UTF-7.
      }

      // Instead, perform the check this way.
      if (enc != null && enc.CodePage == 65000)
      {
          // Encoding is UTF-7.
      }
  }
  ```

- <span data-ttu-id="82c37-142">Se você precisar usar <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> ou <xref:System.Text.UTF7Encoding> :</span><span class="sxs-lookup"><span data-stu-id="82c37-142">If you must use <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> or <xref:System.Text.UTF7Encoding>:</span></span>

  <span data-ttu-id="82c37-143">Você pode suprimir o `SYSLIB0001` aviso no código ou no arquivo *. csproj* do seu projeto.</span><span class="sxs-lookup"><span data-stu-id="82c37-143">You can suppress the `SYSLIB0001` warning in code or within your project's *.csproj* file.</span></span>

  ```csharp
  #pragma warning disable SYSLIB0001 // Disable the warning.
  Encoding enc = Encoding.UTF7;
  #pragma warning restore SYSLIB0001 // Re-enable the warning.
  ```

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
  > <span data-ttu-id="82c37-144">Suprimir `SYSLIB0001` apenas desabilita os <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> <xref:System.Text.UTF7Encoding> avisos e obsoletion.</span><span class="sxs-lookup"><span data-stu-id="82c37-144">Suppressing `SYSLIB0001` only disables the <xref:System.Text.Encoding.UTF7?displayProperty=nameWithType> and <xref:System.Text.UTF7Encoding> obsoletion warnings.</span></span> <span data-ttu-id="82c37-145">Ele não desabilita nenhum outro aviso nem altera o comportamento de APIs como <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="82c37-145">It doesn't disable any other warnings or change the behavior of APIs like <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="82c37-146">Se você precisar dar suporte a `Encoding.GetEncoding("utf-7", ...)` :</span><span class="sxs-lookup"><span data-stu-id="82c37-146">If you must support `Encoding.GetEncoding("utf-7", ...)`:</span></span>

  <span data-ttu-id="82c37-147">Você pode reabilitar o suporte para isso por meio de uma opção de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="82c37-147">You can re-enable support for this via a compatibility switch.</span></span> <span data-ttu-id="82c37-148">Essa opção de compatibilidade pode ser especificada no arquivo *. csproj* do aplicativo ou em um [arquivo de configuração de tempo de execução](../../../../docs/core/run-time-config/index.md), conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="82c37-148">This compatibility switch can be specified in the application's *.csproj* file or in a [run-time configuration file](../../../../docs/core/run-time-config/index.md), as shown in the following examples.</span></span>

  <span data-ttu-id="82c37-149">No arquivo *. csproj* do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="82c37-149">In the application's *.csproj* file:</span></span>

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- Re-enable support for UTF-7 -->
     <EnableUnsafeUTF7Encoding>true</EnableUnsafeUTF7Encoding>
    </PropertyGroup>
  </Project>
  ```

  <span data-ttu-id="82c37-150">Naruntimeconfig.template.jsdo aplicativo *no* arquivo:</span><span class="sxs-lookup"><span data-stu-id="82c37-150">In the application's *runtimeconfig.template.json* file:</span></span>

  ```json
  {
    "configProperties": {
      "System.Text.Encoding.EnableUnsafeUTF7Encoding": true
    }
  }
  ```

  > [!TIP]
  > <span data-ttu-id="82c37-151">Se você reabilitar o suporte para UTF-7, deverá executar uma revisão de segurança do código que chama <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="82c37-151">If you re-enable support for UTF-7, you should perform a security review of code that calls <xref:System.Text.Encoding.GetEncoding%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="82c37-152">Categoria</span><span class="sxs-lookup"><span data-stu-id="82c37-152">Category</span></span>

- <span data-ttu-id="82c37-153">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="82c37-153">Core .NET libraries</span></span>
- <span data-ttu-id="82c37-154">Segurança</span><span class="sxs-lookup"><span data-stu-id="82c37-154">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="82c37-155">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="82c37-155">Affected APIs</span></span>

- <xref:System.Text.Encoding.UTF7?displayProperty=fullName>
- <xref:System.Text.UTF7Encoding.%23ctor>
- <xref:System.Text.UTF7Encoding.%23ctor(System.Boolean)>
- <xref:System.Text.Encoding.GetEncoding(System.Int32)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)?displayProperty=fullName>
- <xref:System.Text.Encoding.GetEncodings?displayProperty=fullName>

<!--

#### Affected APIs

- `System.Text.Encoding.UTF7`
- `System.Text.UTF7Encoding.#ctor`
- `System.Text.UTF7Encoding.#ctor(System.Boolean)`
- `System.Text.Encoding.GetEncoding(System.Int32)`
- `System.Text.Encoding.GetEncoding(System.String)`
- `System.Text.Encoding.GetEncoding(System.Int32,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncoding(System.String,System.Text.EncoderFallback,System.Text.DecoderFallback)`
- `System.Text.Encoding.GetEncodings`

-->
