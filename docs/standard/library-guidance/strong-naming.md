---
title: Nomenclatura forte e bibliotecas do .NET
description: Recomendações de melhores práticas para dar um nome forte a bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: 6f5743c7a8c6fdbdcdcf3aa80d2f92f2e04621f2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201446"
---
# <a name="strong-naming"></a><span data-ttu-id="42f70-103">Nomenclatura forte</span><span class="sxs-lookup"><span data-stu-id="42f70-103">Strong naming</span></span>

<span data-ttu-id="42f70-104">Nomenclatura forte refere-se a assinar um assembly com uma chave, produzindo um [assembly de nome forte](../../framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="42f70-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../../framework/app-domains/strong-named-assemblies.md).</span></span> <span data-ttu-id="42f70-105">Quando um assembly tem um nome forte, ele cria uma identidade exclusiva com base no número de versão de nome e assembly e pode ajudar a evitar conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="42f70-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="42f70-106">A desvantagem de dar um nome forte é que o .NET Framework no Windows habilita carregamento estrito de assemblies depois que um assembly recebe um nome forte.</span><span class="sxs-lookup"><span data-stu-id="42f70-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="42f70-107">Uma referência de assembly de nome forte deve corresponder exatamente à versão referenciada por um assembly, forçando os desenvolvedores a [configurar redirecionamentos de associação](../../framework/configure-apps/redirect-assembly-versions.md) ao usar o assembly:</span><span class="sxs-lookup"><span data-stu-id="42f70-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
         <dependentAssembly>
            <assemblyIdentity name="myAssembly" publicKeyToken="32ab4ba45e0a69a1" culture="neutral" />
            <bindingRedirect oldVersion="1.0.0.0" newVersion="2.0.0.0"/>
         </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="42f70-108">Quando os desenvolvedores do .NET reclamam sobre nomenclatura forte, eles normalmente reclamam de carregamento estrito do assembly.</span><span class="sxs-lookup"><span data-stu-id="42f70-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="42f70-109">Felizmente, esse problema é isolado para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42f70-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="42f70-110">A maioria das outras implementações do .NET, Xamarin, UWP e .NET Core não têm carregamento do assembly estrito e elimina a principal desvantagem da nomenclatura forte.</span><span class="sxs-lookup"><span data-stu-id="42f70-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="42f70-111">Um aspecto importante da nomenclatura forte é que ele é viral: um assembly de nome forte só pode fazer referência outros assemblies de nome forte.</span><span class="sxs-lookup"><span data-stu-id="42f70-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="42f70-112">Se a biblioteca não tiver um nome forte, você terá excluído os desenvolvedores que estão criando um aplicativo ou uma biblioteca que precisa de nomenclatura forte para usá-lo.</span><span class="sxs-lookup"><span data-stu-id="42f70-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="42f70-113">Os benefícios da nomenclatura forte são:</span><span class="sxs-lookup"><span data-stu-id="42f70-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="42f70-114">O assembly pode ser referenciado e usado por outros assemblies de nome forte.</span><span class="sxs-lookup"><span data-stu-id="42f70-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="42f70-115">O assembly pode ser armazenado no GAC (Cache de Assembly Global).</span><span class="sxs-lookup"><span data-stu-id="42f70-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="42f70-116">O assembly pode ser carregado lado a lado com outras versões do assembly.</span><span class="sxs-lookup"><span data-stu-id="42f70-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="42f70-117">Carregamento do assembly lado a lado é normalmente exigido por aplicativos com arquiteturas de plug-in.</span><span class="sxs-lookup"><span data-stu-id="42f70-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="42f70-118">Crie bibliotecas .NET de nome forte</span><span class="sxs-lookup"><span data-stu-id="42f70-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="42f70-119">Você deve dar um nome forte às suas bibliotecas do .NET de software livre.</span><span class="sxs-lookup"><span data-stu-id="42f70-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="42f70-120">Dar um nome forte a um assembly garante que a maioria das pessoas possa usá-lo e o carregamento estrito do assembly afeta apenas o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="42f70-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="42f70-121">Essa orientação é específica para bibliotecas .NET distribuídas publicamente, como bibliotecas .NET publicadas em NuGet.org. Nomenclatura forte não é exigida pela maioria dos aplicativos .NET e não deve ser feita por padrão.</span><span class="sxs-lookup"><span data-stu-id="42f70-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="42f70-122">**✔️ CONSIDERE** dar um nome forte aos assemblies da sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="42f70-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="42f70-123">**✔️ CONSIDERE** adicionar a chave de nome forte ao seu sistema de controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="42f70-123">**✔️ CONSIDER** adding the strong naming key to your source control system.</span></span>

> <span data-ttu-id="42f70-124">Uma chave disponível publicamente permite aos desenvolvedores modificar e recompilar o código-fonte da biblioteca com a mesma chave.</span><span class="sxs-lookup"><span data-stu-id="42f70-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>
> 
> <span data-ttu-id="42f70-125">Você não deverá tornar pública a chave de nome forte se ela tiver sido usada anteriormente para conceder permissões especiais em [cenários de confiança parcial](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span><span class="sxs-lookup"><span data-stu-id="42f70-125">You shouldn't make the strong naming key public if it has been used in the past to give special permissions in [partial-trust scenarios](/dotnet/framework/misc/using-libraries-from-partially-trusted-code).</span></span> <span data-ttu-id="42f70-126">Caso contrário, você poderá comprometer ambientes existentes.</span><span class="sxs-lookup"><span data-stu-id="42f70-126">Otherwise, you might compromise existing environments.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="42f70-127">Quando a identidade do editor do código for desejada, [Authenticode](/windows-hardware/drivers/install/authenticode) e [Assinatura de Pacote do NuGet](/nuget/create-packages/sign-a-package) são recomendados.</span><span class="sxs-lookup"><span data-stu-id="42f70-127">When the identity of the publisher of the code is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="42f70-128">CAS (Segurança de Acesso do Código) não deve ser usada como uma mitigação de segurança.</span><span class="sxs-lookup"><span data-stu-id="42f70-128">Code Access Security (CAS) should not be used as a security mitigation.</span></span>

<span data-ttu-id="42f70-129">**✔️ CONSIDERE** incrementar a versão do assembly nas alterações de versão principal somente para ajudar os usuários a reduzir os redirecionamentos de associação e a frequência com que eles sejam atualizados.</span><span class="sxs-lookup"><span data-stu-id="42f70-129">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="42f70-130">Leia mais sobre [controle de versão e versão do assembly](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="42f70-130">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="42f70-131">**❌ NÃO** adicione, remova nem altere a chave de nome forte.</span><span class="sxs-lookup"><span data-stu-id="42f70-131">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="42f70-132">Modificar a chave de nome forte do assembly muda a identidade do assembly e interrompe o código compilado que a utiliza.</span><span class="sxs-lookup"><span data-stu-id="42f70-132">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="42f70-133">Para obter mais informações, veja [alteração da falha de binário](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="42f70-133">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="42f70-134">**❌ NÃO FAZER** a publicação de versões de nome forte e sem nome forte da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="42f70-134">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="42f70-135">Por exemplo, `Contoso.Api` e `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="42f70-135">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="42f70-136">Publicar dois pacotes bifurca o ecossistema do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="42f70-136">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="42f70-137">Além disso, se um aplicativo acabar dependendo de ambos os pacotes, o desenvolvedor poderá encontrar conflitos de nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="42f70-137">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="42f70-138">No que diz respeito ao .NET, há diferentes tipos em diferentes assemblies.</span><span class="sxs-lookup"><span data-stu-id="42f70-138">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="42f70-139">[Anterior](./cross-platform-targeting.md)
[Próximo](./nuget.md)</span><span class="sxs-lookup"><span data-stu-id="42f70-139">[Previous](./cross-platform-targeting.md)
[Next](./nuget.md)</span></span>
