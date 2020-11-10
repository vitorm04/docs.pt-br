---
title: "NETSDK1071: um PackageReference para ' {0} ' especificou uma versão de `{1}` ."
description: Como resolver o problema de um PackageReference para um metapacote incluído com a estrutura com uma versão.
author: Forgind
ms.topic: error-reference
ms.date: 10/09/2020
f1_keywords:
- NETSDK1071
ms.openlocfilehash: 852232cba04bb93a17872280e10848c2896991ae
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445744"
---
# <a name="netsdk1071-explicitly-versioned-packagereference-to-a-metapackage-that-would-be-included-with-the-framework"></a><span data-ttu-id="a9270-103">NETSDK1071: PackageReference com controle de versão explícito para um metapacote que seria incluído com a estrutura.</span><span class="sxs-lookup"><span data-stu-id="a9270-103">NETSDK1071: Explicitly versioned PackageReference to a metapackage that would be included with the framework.</span></span>

<span data-ttu-id="a9270-104">**Este artigo aplica-se a:** ✔️ o SDK do .NET 5.0.100 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="a9270-104">**This article applies to:** ✔️ .NET 5.0.100 SDK and later versions</span></span>

<span data-ttu-id="a9270-105">Quando o SDK do .NET emite aviso NETSDK1071, ele sugere que pode haver um conflito de versão no futuro entre a versão de um metapacote especificado em um PackageReference e a versão desse metapacote como referenciado implicitamente por meio de uma propriedade TargetFramework:</span><span class="sxs-lookup"><span data-stu-id="a9270-105">When the .NET SDK issues warning NETSDK1071, it suggests there may be a version conflict in the future between the version of a metapackage specified in a PackageReference and the version of that metapackage as implicitly referenced via a TargetFramework property:</span></span>

```xml
<PropertyGroup>
  <TargetFramework>netcoreapp3.1</TargetFramework>
</PropertyGroup>
```

<span data-ttu-id="a9270-106">Como o TargetFramework automaticamente coloca em uma versão do metapacote, as versões entrarão em conflito caso sejam diferentes.</span><span class="sxs-lookup"><span data-stu-id="a9270-106">Since the TargetFramework automatically brings in a version of the metapackage, the versions will conflict should they ever differ.</span></span>

<span data-ttu-id="a9270-107">Para resolver esse problema:</span><span class="sxs-lookup"><span data-stu-id="a9270-107">To resolve this:</span></span>

1. <span data-ttu-id="a9270-108">Considere, ao direcionar .NET Core ou .NET Standard, evitando referências explícitas para `Microsoft.NETCore.App` ou `NETStandard.Library` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="a9270-108">Consider, when targeting .NET Core or .NET Standard, avoiding explicit references to `Microsoft.NETCore.App` or `NETStandard.Library` in your project file.</span></span>
2. <span data-ttu-id="a9270-109">Se você precisar de uma versão específica do tempo de execução ao direcionar para o .NET Core, use a `<RuntimeFrameworkVersion>` propriedade em vez de fazer referência ao metapacote diretamente.</span><span class="sxs-lookup"><span data-stu-id="a9270-109">If you need a specific version of the runtime when targeting .NET Core, use the `<RuntimeFrameworkVersion>`property instead of referencing the metapackage directly.</span></span> <span data-ttu-id="a9270-110">Por exemplo, isso pode acontecer se você estiver usando [implantações independentes](../../deploying/index.md#publish-self-contained) e precisar de um patch específico do tempo de execução do 1.0.0 LTS.</span><span class="sxs-lookup"><span data-stu-id="a9270-110">As an example, this could happen if you're using [self-contained deployments](../../deploying/index.md#publish-self-contained) and need a specific patch of the 1.0.0 LTS runtime.</span></span>
3. <span data-ttu-id="a9270-111">Se precisar de uma versão específica do `NetStandard.Library` ao direcionar .net Standard, você poderá usar a `<NetStandardImplicitPackageVersion>` propriedade e defini-la para a versão necessária.</span><span class="sxs-lookup"><span data-stu-id="a9270-111">If you need a specific version of `NetStandard.Library` when targeting .NET Standard, you can use the `<NetStandardImplicitPackageVersion>` property and set it to the version you need.</span></span>
4. <span data-ttu-id="a9270-112">Não eplicitly adicionar ou atualizar referências a um `Microsoft.NETCore.App` ou `NETSTandard.Library` em projetos .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a9270-112">Don't eplicitly add or update references to either `Microsoft.NETCore.App` or `NETSTandard.Library` in .NET Framework projects.</span></span> <span data-ttu-id="a9270-113">O NuGet instala automaticamente qualquer versão de `NETStandard.Library` que você precisa ao usar um pacote NuGet baseado em .net Standard.</span><span class="sxs-lookup"><span data-stu-id="a9270-113">NuGet automatically installs any version of `NETStandard.Library` you need when using a .NET Standard-based NuGet package.</span></span>
5. <span data-ttu-id="a9270-114">Não especifique uma versão para `Microsoft.AspNetCore.App` o ou `Microsoft.AspNetCore.All` ao usar o .NET Core 2.1 +, pois o SDK do .NET Core seleciona automaticamente a versão apropriada.</span><span class="sxs-lookup"><span data-stu-id="a9270-114">Do not specify a version for `Microsoft.AspNetCore.App` or `Microsoft.AspNetCore.All` when using .NET Core 2.1+, as the .NET Core SDK automatically selects the appropriate version.</span></span> <span data-ttu-id="a9270-115">(Observação: isso só funcionará ao direcionar o .NET Core 2,1 se o projeto também usar `Microsoft.NET.Sdk.Web` .</span><span class="sxs-lookup"><span data-stu-id="a9270-115">(Note: This only works when targeting .NET Core 2.1 if the project also uses `Microsoft.NET.Sdk.Web`.</span></span> <span data-ttu-id="a9270-116">Esse problema foi resolvido no SDK do .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="a9270-116">This problem was resolved in the .NET Core 2.2 SDK.)</span></span>
6. <span data-ttu-id="a9270-117">Se você quiser que o aviso saia, também poderá desabilitá-lo:</span><span class="sxs-lookup"><span data-stu-id="a9270-117">If you want the warning to go away, you can also disable it:</span></span>

   ```xml
   <PackageReference Include="Microsoft.NetCore.App" Version="2.2.8" >
     <AllowExplicitVersion>true</AllowExplicitVersion>
   </PackageReference>
   ```
