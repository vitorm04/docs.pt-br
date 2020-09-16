---
ms.openlocfilehash: 7cb146d19486618a4cee9976abe2220ea4b72790
ms.sourcegitcommit: d337df55f83325918cbbd095eb573400bea49064
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2020
ms.locfileid: "88204031"
---
### <a name="binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps"></a><span data-ttu-id="f88ac-101">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f88ac-101">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>

<span data-ttu-id="f88ac-102">`Serialize` e `Deserialize` métodos em <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , <xref:System.Runtime.Serialization.Formatter> e <xref:System.Runtime.Serialization.IFormatter> agora são obsoletos.</span><span class="sxs-lookup"><span data-stu-id="f88ac-102">`Serialize` and `Deserialize` methods on <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, <xref:System.Runtime.Serialization.Formatter>, and <xref:System.Runtime.Serialization.IFormatter> are now obsolete.</span></span> <span data-ttu-id="f88ac-103">Além disso, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a serialização é proibida por padrão para aplicativos ASP.net.</span><span class="sxs-lookup"><span data-stu-id="f88ac-103">Additionally, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serialization is prohibited by default for ASP.NET apps.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f88ac-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="f88ac-104">Change description</span></span>

<span data-ttu-id="f88ac-105">Devido a [vulnerabilidades de segurança](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) no <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> , os métodos a seguir agora são obsoletos.</span><span class="sxs-lookup"><span data-stu-id="f88ac-105">Due to [security vulnerabilities](../../../../docs/standard/serialization/binaryformatter-security-guide.md#binaryformatter-security-vulnerabilities) in <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, the following methods are now obsolete.</span></span> <span data-ttu-id="f88ac-106">Além disso, no ASP.NET Core 5,0 e em aplicativos posteriores, eles lançarão um <xref:System.NotSupportedException> , a menos que o aplicativo Web tenha reativado a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> funcionalidade.</span><span class="sxs-lookup"><span data-stu-id="f88ac-106">Additionally, in ASP.NET Core 5.0 and later apps, they will throw a <xref:System.NotSupportedException>, unless the web app has re-enabled <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> functionality.</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType>

<span data-ttu-id="f88ac-107">Esses métodos são marcados como obsoletos como parte de um esforço para o uso do vento <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> no ecossistema do .net.</span><span class="sxs-lookup"><span data-stu-id="f88ac-107">These methods are marked obsolete as part of an effort to wind down usage of <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> within the .NET ecosystem.</span></span>

<span data-ttu-id="f88ac-108">Os métodos de serialização a seguir também são obsoletos, mas não têm nenhuma alteração comportamental:</span><span class="sxs-lookup"><span data-stu-id="f88ac-108">The following serialization methods are also now obsolete, but have no behavioral changes:</span></span>

- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType>

#### <a name="version-introduced"></a><span data-ttu-id="f88ac-109">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="f88ac-109">Version introduced</span></span>

<span data-ttu-id="f88ac-110">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="f88ac-110">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f88ac-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="f88ac-111">Recommended action</span></span>

- <span data-ttu-id="f88ac-112">Pare <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> de usar no seu código.</span><span class="sxs-lookup"><span data-stu-id="f88ac-112">Stop using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in your code.</span></span> <span data-ttu-id="f88ac-113">Em vez disso, considere usar <xref:System.Text.Json.JsonSerializer> ou <xref:System.Xml.Serialization.XmlSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f88ac-113">Instead, consider using <xref:System.Text.Json.JsonSerializer> or <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f88ac-114">Para obter mais informações, consulte [Guia de segurança do BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="f88ac-114">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

- <span data-ttu-id="f88ac-115">Você pode suprimir temporariamente o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> aviso de tempo de compilação, que é `SYSLIB0011` .</span><span class="sxs-lookup"><span data-stu-id="f88ac-115">You can temporarily suppress the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> compile-time warning, which is `SYSLIB0011`.</span></span> <span data-ttu-id="f88ac-116">Recomendamos que você avalie minuciosamente seu código em busca de riscos antes de escolher essa opção.</span><span class="sxs-lookup"><span data-stu-id="f88ac-116">We recommend that you thoroughly assess your code for risks before choosing this option.</span></span> <span data-ttu-id="f88ac-117">A maneira mais fácil de suprimir os avisos é envolver o site de chamada individual com `#pragma` diretivas.</span><span class="sxs-lookup"><span data-stu-id="f88ac-117">The easiest way to suppress the warnings is to surround the individual call site with `#pragma` directives.</span></span>

  ```csharp
  // Now read the purchase order back from disk
  using (var readStream = new FileStream("myfile.bin", FileMode.Open))
  {
      var formatter = new BinaryFormatter();
  #pragma warning disable SYSLIB0011
      return (PurchaseOrder)formatter.Deserialize(readStream);
  #pragma warning restore SYSLIB0011
  }
  ```

  <span data-ttu-id="f88ac-118">Você também pode suprimir o aviso no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f88ac-118">You can also suppress the warning in the project file.</span></span>

  ```xml
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Disable "BinaryFormatter is obsolete" warnings for entire project -->
    <NoWarn>$(NoWarn);SYSLIB0011</NoWarn>
  </PropertyGroup>
  ```

  <span data-ttu-id="f88ac-119">Se você suprimir o aviso no arquivo de projeto, o aviso será suprimido para todos os arquivos de código no projeto.</span><span class="sxs-lookup"><span data-stu-id="f88ac-119">If you suppress the warning in the project file, the warning is suppressed for all code files in the project.</span></span> <span data-ttu-id="f88ac-120">Suprimir SYSLIB0011 não suprime avisos causados por outras APIs obsoletas.</span><span class="sxs-lookup"><span data-stu-id="f88ac-120">Suppressing SYSLIB0011 does not suppress warnings caused by using other obsolete APIs.</span></span>

- <span data-ttu-id="f88ac-121">Para continuar usando <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> o em aplicativos ASP.net, você pode reabilitá-lo no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f88ac-121">To continue using <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> in ASP.NET apps, you can re-enable it in the project file.</span></span> <span data-ttu-id="f88ac-122">No entanto, é altamente recomendável não fazer isso.</span><span class="sxs-lookup"><span data-stu-id="f88ac-122">However, it's strongly recommended not to do this.</span></span> <span data-ttu-id="f88ac-123">Para obter mais informações, consulte [Guia de segurança do BinaryFormatter](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span><span class="sxs-lookup"><span data-stu-id="f88ac-123">For more information, see [BinaryFormatter security guide](../../../../docs/standard/serialization/binaryformatter-security-guide.md).</span></span>

  ```xml
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
    <!-- Warning: Setting the following switch is *NOT* recommended in web apps. -->
    <EnableUnsafeBinaryFormatterSerialization>true</EnableUnsafeBinaryFormatterSerialization>
  </PropertyGroup>
  ```

<span data-ttu-id="f88ac-124">Para obter mais informações sobre as ações recomendadas, consulte [Resolvendo erros de BinaryFormatter obsoletion e de desativação](https://aka.ms/binaryformatter).</span><span class="sxs-lookup"><span data-stu-id="f88ac-124">For more information about recommended actions, see [Resolving BinaryFormatter obsoletion and disablement errors](https://aka.ms/binaryformatter).</span></span>

#### <a name="category"></a><span data-ttu-id="f88ac-125">Categoria</span><span class="sxs-lookup"><span data-stu-id="f88ac-125">Category</span></span>

- <span data-ttu-id="f88ac-126">Bibliotecas principais do .NET</span><span class="sxs-lookup"><span data-stu-id="f88ac-126">Core .NET libraries</span></span>
- <span data-ttu-id="f88ac-127">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f88ac-127">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f88ac-128">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="f88ac-128">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=fullName>
- <xref:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Serialize`
- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`
- `M:System.Runtime.Serialization.Formatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.Formatter.Deserialize(System.IO.Stream)`
- `M:System.Runtime.Serialization.IFormatter.Serialize(System.IO.Stream,System.Object)`
- `M:System.Runtime.Serialization.IFormatter.Deserialize(System.IO.Stream)`

-->
