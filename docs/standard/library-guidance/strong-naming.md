---
title: Nomenclatura forte e bibliotecas do .NET
description: Práticas recomendadas para bibliotecas do .NET de nomeação forte.
author: jamesnk
ms.author: mairaw
ms.date: 10/16/2018
ms.openlocfilehash: e3f7d443eb9acc84c800ea2611b803733085391c
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372798"
---
# <a name="strong-naming"></a><span data-ttu-id="7be8e-103">Nomenclatura forte</span><span class="sxs-lookup"><span data-stu-id="7be8e-103">Strong naming</span></span>

<span data-ttu-id="7be8e-104">Nomenclatura forte refere-se ao assinar um assembly com uma chave, produzindo uma [assembly de nome forte](../../framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7be8e-104">Strong naming refers to signing an assembly with a key, producing a [strong-named assembly](../../framework/app-domains/strong-named-assemblies.md).</span></span> <span data-ttu-id="7be8e-105">Quando um assembly é o nome forte, ele cria uma identidade exclusiva com base no número de versão de nome e o assembly, e ele pode ajudar a evitar conflitos de assembly.</span><span class="sxs-lookup"><span data-stu-id="7be8e-105">When an assembly is strong-named, it creates a unique identity based on the name and assembly version number, and it can help prevent assembly conflicts.</span></span>

<span data-ttu-id="7be8e-106">A desvantagem de nomenclatura forte é que o .NET Framework no Windows permite estrito carregamento de assemblies depois que um assembly um nome forte.</span><span class="sxs-lookup"><span data-stu-id="7be8e-106">The downside to strong naming is that the .NET Framework on Windows enables strict loading of assemblies once an assembly is strong named.</span></span> <span data-ttu-id="7be8e-107">Uma referência de assembly de nome forte deve corresponder exatamente a versão referenciada por um assembly, forçar os desenvolvedores a [configurar redirecionamentos de associação](../../framework/configure-apps/redirect-assembly-versions.md) ao usar o assembly:</span><span class="sxs-lookup"><span data-stu-id="7be8e-107">A strong-named assembly reference must exactly match the version referenced by an assembly, forcing developers to [configure binding redirects](../../framework/configure-apps/redirect-assembly-versions.md) when using the assembly:</span></span>

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

<span data-ttu-id="7be8e-108">Quando os desenvolvedores de .NET reclamarem sobre nomenclatura forte, o que eles reclamar sobre geralmente é estrito carregamento do assembly.</span><span class="sxs-lookup"><span data-stu-id="7be8e-108">When .NET developers complain about strong naming, what they're usually complaining about is strict assembly loading.</span></span> <span data-ttu-id="7be8e-109">Felizmente, esse problema é isolado para o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7be8e-109">Fortunately, this issue is isolated to the .NET Framework.</span></span> <span data-ttu-id="7be8e-110">A maioria das outras implementações do .NET, Xamarin, UWP e .NET core não tiver o carregamento do assembly estrito e remove a principal desvantagem da nomenclatura forte.</span><span class="sxs-lookup"><span data-stu-id="7be8e-110">.NET Core, Xamarin, UWP, and most other .NET implementations don't have strict assembly loading and removes the main downside of strong naming.</span></span>

<span data-ttu-id="7be8e-111">Um aspecto importante da nomenclatura forte é que ele é viral: um nome forte assembly só podem fazer referência outros forte conjuntos nomeados.</span><span class="sxs-lookup"><span data-stu-id="7be8e-111">One important aspect of strong naming is that it's viral: a strong named assembly can only reference other strong named assemblies.</span></span> <span data-ttu-id="7be8e-112">Se sua biblioteca não é forte nomeado, você excluiu os desenvolvedores que estão criando um aplicativo ou uma biblioteca que precisa de nomenclatura forte de usá-lo.</span><span class="sxs-lookup"><span data-stu-id="7be8e-112">If your library isn't strong named, then you have excluded developers who are building an application or library that needs strong naming from using it.</span></span>

<span data-ttu-id="7be8e-113">Os benefícios da nomenclatura forte são:</span><span class="sxs-lookup"><span data-stu-id="7be8e-113">The benefits of strong naming are:</span></span>

1. <span data-ttu-id="7be8e-114">O assembly pode ser referenciado e usado por outros assemblies de nome forte.</span><span class="sxs-lookup"><span data-stu-id="7be8e-114">The assembly can be referenced and used by other strong-named assemblies.</span></span>
2. <span data-ttu-id="7be8e-115">O assembly pode ser armazenado no Cache de Assembly Global (GAC).</span><span class="sxs-lookup"><span data-stu-id="7be8e-115">The assembly can be stored in the Global Assembly Cache (GAC).</span></span>
3. <span data-ttu-id="7be8e-116">O assembly pode ser carregado lado a lado com outras versões do assembly.</span><span class="sxs-lookup"><span data-stu-id="7be8e-116">The assembly can be loaded side by side with other versions of the assembly.</span></span> <span data-ttu-id="7be8e-117">Carregamento do assembly lado a lado é normalmente exigido por aplicativos com arquiteturas de plug-in.</span><span class="sxs-lookup"><span data-stu-id="7be8e-117">Side-by-side assembly loading is commonly required by applications with plug-in architectures.</span></span>

## <a name="create-strong-named-net-libraries"></a><span data-ttu-id="7be8e-118">Crie um forte chamado bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="7be8e-118">Create strong named .NET libraries</span></span>

<span data-ttu-id="7be8e-119">Forte, você deve nomear suas bibliotecas do .NET de código-fonte aberto.</span><span class="sxs-lookup"><span data-stu-id="7be8e-119">You should strong name your open-source .NET libraries.</span></span> <span data-ttu-id="7be8e-120">Um assembly de nomenclatura forte garante que a maioria das pessoas pode usá-lo e estrito assembly carregar somente afeta o .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7be8e-120">Strong naming an assembly ensures the most people can use it, and strict assembly loading only affects the .NET Framework.</span></span>

> [!NOTE]
> <span data-ttu-id="7be8e-121">Neste guia é específico para bibliotecas .NET distribuídas publicamente, como bibliotecas .NET publicados em NuGet.org. Nomenclatura forte não é exigido pela maioria dos aplicativos .NET e não deve ser feita por padrão.</span><span class="sxs-lookup"><span data-stu-id="7be8e-121">This guidance is specific to publicly distributed .NET libraries, such as .NET libraries published on NuGet.org. Strong naming is not required by most .NET applications and should not be done by default.</span></span>

<span data-ttu-id="7be8e-122">**Considere a possibilidade de ✔️** forte nomear os assemblies da sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7be8e-122">**✔️ CONSIDER** strong naming your library's assemblies.</span></span>

<span data-ttu-id="7be8e-123">**Considere a possibilidade de ✔️** fazer check-in a chave usada para o nome forte em seu sistema de controle de origem.</span><span class="sxs-lookup"><span data-stu-id="7be8e-123">**✔️ CONSIDER** checking in the key used to strong name into your source control system.</span></span>

> <span data-ttu-id="7be8e-124">Uma chave disponível publicamente permite aos desenvolvedores modificar e recompilar seu código-fonte de biblioteca com a mesma chave.</span><span class="sxs-lookup"><span data-stu-id="7be8e-124">A publicly available key lets developers modify and recompile your library source code with the same key.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7be8e-125">Quando uma identidade de criptografia for desejada, [Authenticode](/windows-hardware/drivers/install/authenticode) e [assinatura de pacote do NuGet](/nuget/create-packages/sign-a-package) são recomendados.</span><span class="sxs-lookup"><span data-stu-id="7be8e-125">When a cryptographic identity is desired, [Authenticode](/windows-hardware/drivers/install/authenticode) and [NuGet Package Signing](/nuget/create-packages/sign-a-package) are recommended.</span></span> <span data-ttu-id="7be8e-126">Nomenclatura forte não deve ser usado para considerações de segurança.</span><span class="sxs-lookup"><span data-stu-id="7be8e-126">Strong naming should not be used for security considerations.</span></span>

<span data-ttu-id="7be8e-127">**Considere a possibilidade de ✔️** incrementar a versão do assembly nas alterações de versão principal somente para ajudar os usuários a reduzir os redirecionamentos de associação e a frequência com que eles sejam atualizados.</span><span class="sxs-lookup"><span data-stu-id="7be8e-127">**✔️ CONSIDER** incrementing the assembly version on only major version changes to help users reduce binding redirects, and how often they're updated.</span></span>

> <span data-ttu-id="7be8e-128">Leia mais sobre [controle de versão e a versão do assembly](./versioning.md#assembly-version).</span><span class="sxs-lookup"><span data-stu-id="7be8e-128">Read more about [versioning and the assembly version](./versioning.md#assembly-version).</span></span>

<span data-ttu-id="7be8e-129">**❌ NÃO** adicionar, remover ou alterar a chave de nomeação forte.</span><span class="sxs-lookup"><span data-stu-id="7be8e-129">**❌ DO NOT** add, remove, or change the strong naming key.</span></span>

> <span data-ttu-id="7be8e-130">Modificando a chave de nomenclatura forte do assembly é alterado na identidade do assembly e interrompe o código compilado que o utiliza.</span><span class="sxs-lookup"><span data-stu-id="7be8e-130">Modifying an assembly's strong naming key changes the assembly's identity and breaks compiled code that uses it.</span></span> <span data-ttu-id="7be8e-131">Para obter mais informações, consulte [binário alterações significativas](./breaking-changes.md#binary-breaking-change).</span><span class="sxs-lookup"><span data-stu-id="7be8e-131">For more information, see [binary breaking changes](./breaking-changes.md#binary-breaking-change).</span></span>

<span data-ttu-id="7be8e-132">**❌ NÃO** publicar versões de nome forte e sem nome forte da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7be8e-132">**❌ DO NOT** publish strong-named and non-strong-named versions of your library.</span></span> <span data-ttu-id="7be8e-133">Por exemplo, `Contoso.Api` e `Contoso.Api.StrongNamed`.</span><span class="sxs-lookup"><span data-stu-id="7be8e-133">For example, `Contoso.Api` and `Contoso.Api.StrongNamed`.</span></span>

> <span data-ttu-id="7be8e-134">Publicando duas bifurcações de pacotes em seu sistema de eco do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="7be8e-134">Publishing two packages forks your developer eco-system.</span></span> <span data-ttu-id="7be8e-135">Além disso, se um aplicativo acaba dependendo de ambos os pacotes de desenvolvedor pode encontrar conflitos de nome de tipo.</span><span class="sxs-lookup"><span data-stu-id="7be8e-135">Also, if an application ends up depending on both packages the developer can encounter type name conflicts.</span></span> <span data-ttu-id="7be8e-136">Que diz respeito ao .NET são tipos diferentes em diferentes assemblies.</span><span class="sxs-lookup"><span data-stu-id="7be8e-136">As far as .NET is concerned they are different types in different assemblies.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7be8e-137">[Anterior](./cross-platform-targeting.md)
[Próximo](./nuget.md)</span><span class="sxs-lookup"><span data-stu-id="7be8e-137">[Previous](./cross-platform-targeting.md)
[Next](./nuget.md)</span></span>
