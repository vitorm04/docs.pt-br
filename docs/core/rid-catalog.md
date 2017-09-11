---
title: "Catálogo do RID (Identificador de Tempo de Execução) do .NET Core"
description: "Saiba mais sobre o RID (Identificador de tempo de execução) e como os RIDs são usados no .NET Core."
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/22/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b2032f5d-771f-48d9-917c-587d9509035c
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 3490fb639efd223dc36190324bdf3a06bc23c10e
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="net-core-runtime-identifier-rid-catalog"></a><span data-ttu-id="fc184-104">Catálogo do RID (Identificador de Tempo de Execução) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fc184-104">.NET Core Runtime IDentifier (RID) catalog</span></span>

## <a name="what-are-rids"></a><span data-ttu-id="fc184-105">O que são RIDs?</span><span class="sxs-lookup"><span data-stu-id="fc184-105">What are RIDs?</span></span>
<span data-ttu-id="fc184-106">RID é a abreviação de *Identificador de Tempo de Execução*.</span><span class="sxs-lookup"><span data-stu-id="fc184-106">RID is short for *Runtime IDentifier*.</span></span> <span data-ttu-id="fc184-107">RIDs são usados para identificar os sistemas operacionais de destino em que um aplicativo ou ativo (ou seja, o assembly) será executado.</span><span class="sxs-lookup"><span data-stu-id="fc184-107">RIDs are used to identify target operating systems where an application or asset (that is, assembly) will run.</span></span> <span data-ttu-id="fc184-108">Eles assemelham-se a: "ubuntu.14.04-x64", "win7-x64" e "osx.10.11-x64".</span><span class="sxs-lookup"><span data-stu-id="fc184-108">They look like this: "ubuntu.14.04-x64", "win7-x64", "osx.10.11-x64".</span></span> <span data-ttu-id="fc184-109">Para os pacotes com dependências nativas, ele designará as plataformas em que o pacote pode ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="fc184-109">For the packages with native dependencies, it will designate on which platforms the package can be restored.</span></span> 

<span data-ttu-id="fc184-110">É importante observar que os RIDs são cadeias de caracteres realmente opacas.</span><span class="sxs-lookup"><span data-stu-id="fc184-110">It is important to note that RIDs are really opaque strings.</span></span> <span data-ttu-id="fc184-111">Isso significa que eles devem corresponder exatamente para as operações que os utilizam poderem funcionar.</span><span class="sxs-lookup"><span data-stu-id="fc184-111">This means that they have to match exactly for operations using them to work.</span></span> <span data-ttu-id="fc184-112">Por exemplo, vamos considerar o caso do [Elementary OS](https://elementary.io/), que é um clone simples do Ubuntu 14.04.</span><span class="sxs-lookup"><span data-stu-id="fc184-112">As an example, let us consider the case of [Elementary OS](https://elementary.io/), which is a straightforward clone of Ubuntu 14.04.</span></span> <span data-ttu-id="fc184-113">Embora .NET Core e CLI funcionem nessa versão do Ubuntu, se você tentar usá-los no Elementary OS sem modificações, a operação de restauração de qualquer pacote falhará.</span><span class="sxs-lookup"><span data-stu-id="fc184-113">Although .NET Core and CLI work on top of that version of Ubuntu, if you try to use them on Elementary OS without any modifications, the restore operation for any package will fail.</span></span> <span data-ttu-id="fc184-114">Isso ocorre porque atualmente não temos um RID que designa o Elementary OS como uma plataforma.</span><span class="sxs-lookup"><span data-stu-id="fc184-114">This is because we currently don't have a RID that designates Elementary OS as a platform.</span></span> 

<span data-ttu-id="fc184-115">RIDs que representem sistemas operacionais concretos geralmente seguem este padrão: `[os].[version]-[arch]` em que:</span><span class="sxs-lookup"><span data-stu-id="fc184-115">RIDs that represent concrete operating systems usually follow this pattern: `[os].[version]-[arch]` where:</span></span>
- <span data-ttu-id="fc184-116">`[os]` é o moniker do sistema operacional, por exemplo, `ubuntu`.</span><span class="sxs-lookup"><span data-stu-id="fc184-116">`[os]` is the operating system moniker, for example, `ubuntu`.</span></span>
- <span data-ttu-id="fc184-117">`[version]` é a versão do sistema operacional na forma de um número de versão separado por ponto (`.`), por exemplo, `15.10`, preciso o suficiente para permitir que ativos sejam direcionados para as APIs da plataforma do sistema operacional representado por essa versão.</span><span class="sxs-lookup"><span data-stu-id="fc184-117">`[version]` is the operating system version in the form of a dot (`.`) separated version number, for example, `15.10`, accurate enough to reasonably enable assets to target operating system platform APIs represented by that version.</span></span>
  - <span data-ttu-id="fc184-118">Elas **não** devem ser versões comerciais, pois essas geralmente representam várias versões distintas do sistema operacional com diferentes áreas de superfície de API da plataforma.</span><span class="sxs-lookup"><span data-stu-id="fc184-118">This **shouldn't** be marketing versions, as they often represent multiple discrete versions of the operating system with varying platform API surface area.</span></span>
- <span data-ttu-id="fc184-119">`[arch]` é a arquitetura do processador, por exemplo, `x86`, `x64`, `arm`, `arm64` etc.</span><span class="sxs-lookup"><span data-stu-id="fc184-119">`[arch]` is the processor architecture, for example, `x86`, `x64`, `arm`, `arm64`, etc.</span></span>

<span data-ttu-id="fc184-120">O gráfico RID é definido em um pacote chamado `Microsoft.NETCore.Platforms` em um arquivo chamado `runtime.json`, que você pode encontrar no [repositório CoreFX](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json).</span><span class="sxs-lookup"><span data-stu-id="fc184-120">The RID graph is defined in a package called `Microsoft.NETCore.Platforms` in a file called `runtime.json`, which you can see on the [CoreFX repo](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json).</span></span> <span data-ttu-id="fc184-121">Se você usar esse arquivo, notará que alguns RIDs têm uma instrução `"#import"`.</span><span class="sxs-lookup"><span data-stu-id="fc184-121">If you use this file, you will notice that some of the RIDs have an `"#import"` statement in them.</span></span> <span data-ttu-id="fc184-122">Essas são instruções de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="fc184-122">These statements are compatibility statements.</span></span> <span data-ttu-id="fc184-123">Isso significa que um RID que contém um RID importado pode ser direcionado para restaurar pacotes para esse RID.</span><span class="sxs-lookup"><span data-stu-id="fc184-123">That means that a RID that has an imported RID in it can be a target for restoring packages for that RID.</span></span> <span data-ttu-id="fc184-124">Parece um pouco confuso, mas vejamos um exemplo.</span><span class="sxs-lookup"><span data-stu-id="fc184-124">Slightly confusing, but let's look at an example.</span></span> <span data-ttu-id="fc184-125">Vamos dar uma olhada no macOS:</span><span class="sxs-lookup"><span data-stu-id="fc184-125">Let's take a look at macOS:</span></span>

```json
"osx.10.11-x64": {
    "#import": [ "osx.10.11", "osx.10.10-x64" ]
}
```
<span data-ttu-id="fc184-126">O RID acima especifica que `osx.10.11-x64` importa `osx.10.10-x64`.</span><span class="sxs-lookup"><span data-stu-id="fc184-126">The above RID specifies that `osx.10.11-x64` imports `osx.10.10-x64`.</span></span> <span data-ttu-id="fc184-127">Isso significa que, ao restaurar pacotes, o NuGet poderá restaurar pacotes que especificam que precisam de `osx.10.10-x64` em `osx.10.11-x64`.</span><span class="sxs-lookup"><span data-stu-id="fc184-127">This means that when restoring packages, NuGet will be able to restore packages that specify that they need `osx.10.10-x64` on `osx.10.11-x64`.</span></span>

<span data-ttu-id="fc184-128">Um exemplo de gráfico RID ligeiramente maior:</span><span class="sxs-lookup"><span data-stu-id="fc184-128">A slightly bigger example RID graph:</span></span>  

- `win10-arm`
  - `win10`
  - `win81-arm`
    - `win81`
    - `win8-arm`
      - `win8`
        - `win7`
          - `win`
            - `any`

<span data-ttu-id="fc184-129">Todos os RIDs eventualmente mapeiam para a raiz de `any` RID.</span><span class="sxs-lookup"><span data-stu-id="fc184-129">All RIDs eventually map back to the root `any` RID.</span></span>

<span data-ttu-id="fc184-130">Embora pareça fácil de usar, existem algumas coisas especiais sobre RIDs que você precisa ter em mente ao trabalhar com eles:</span><span class="sxs-lookup"><span data-stu-id="fc184-130">Although they look easy enough to use, there are some special things about RIDs that you have to keep in mind when working with them:</span></span>

* <span data-ttu-id="fc184-131">Eles são **cadeias de caracteres opacas** e devem ser tratados como caixas pretas</span><span class="sxs-lookup"><span data-stu-id="fc184-131">They are **opaque strings** and should be treated as black boxes</span></span>
    * <span data-ttu-id="fc184-132">Você não deve criar RIDs programaticamente</span><span class="sxs-lookup"><span data-stu-id="fc184-132">You should not construct RIDs programmatically</span></span>
* <span data-ttu-id="fc184-133">Você precisa usar os RIDs que já estão definidos para a plataforma e este documento mostra isso</span><span class="sxs-lookup"><span data-stu-id="fc184-133">You need to use the RIDs that are already defined for the platform and this document shows that</span></span>
* <span data-ttu-id="fc184-134">Os RIDs precisam ser específicos, por isso não crie suposições com base no valor do real do RID. Consulte este documento para determinar qual RID(s) são necessário para uma determinada plataforma</span><span class="sxs-lookup"><span data-stu-id="fc184-134">The RIDs do need to be specific so don't assume anything from the actual RID value; please consult this document to determine which RID(s) you need for a given platform</span></span>

## <a name="using-rids"></a><span data-ttu-id="fc184-135">Usando RIDs</span><span class="sxs-lookup"><span data-stu-id="fc184-135">Using RIDs</span></span>
<span data-ttu-id="fc184-136">Para usar RIDs, você precisa saber quais RIDs existem.</span><span class="sxs-lookup"><span data-stu-id="fc184-136">In order to use RIDs, you have to know which RIDs there are.</span></span> <span data-ttu-id="fc184-137">Novos RIDs são adicionados regularmente para a plataforma.</span><span class="sxs-lookup"><span data-stu-id="fc184-137">New RIDs are added regularly to the platform.</span></span> <span data-ttu-id="fc184-138">Para a versão mais recente, consulte o arquivo [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) no repositório CoreFX.</span><span class="sxs-lookup"><span data-stu-id="fc184-138">For the latest version, please check the [runtime.json](https://github.com/dotnet/corefx/blob/master/pkg/Microsoft.NETCore.Platforms/runtime.json) file on CoreFX repo.</span></span>

> [!NOTE]
> <span data-ttu-id="fc184-139">Estamos trabalhando para disponibilizar essas informações em um formato mais interativo.</span><span class="sxs-lookup"><span data-stu-id="fc184-139">We are working towards getting this information into a more interactive form.</span></span> <span data-ttu-id="fc184-140">Quando isso acontecer, esta página será atualizada para indicar a essa ferramenta e/ou sua documentação de uso.</span><span class="sxs-lookup"><span data-stu-id="fc184-140">When that happens, this page will be updated to point to that tool and/or its usage documentation.</span></span> 

## <a name="windows-rids"></a><span data-ttu-id="fc184-141">RIDs do Windows</span><span class="sxs-lookup"><span data-stu-id="fc184-141">Windows RIDs</span></span>

* <span data-ttu-id="fc184-142">Windows 7 / Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="fc184-142">Windows 7 / Windows Server 2008 R2</span></span>
    * `win7-x64`
    * `win7-x86`
* <span data-ttu-id="fc184-143">Windows 8 / Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="fc184-143">Windows 8 / Windows Server 2012</span></span>
    * `win8-x64`
    * `win8-x86`
    * `win8-arm`
* <span data-ttu-id="fc184-144">Windows 8.1 / Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="fc184-144">Windows 8.1 / Windows Server 2012 R2</span></span>
    * `win81-x64`
    * `win81-x86`
    * `win81-arm`
* <span data-ttu-id="fc184-145">Windows 10 / Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="fc184-145">Windows 10 / Windows Server 2016</span></span>
    * `win10-x64`
    * `win10-x86`
    * `win10-arm`
    * `win10-arm64`

## <a name="linux-rids"></a><span data-ttu-id="fc184-146">RIDs do Linux</span><span class="sxs-lookup"><span data-stu-id="fc184-146">Linux RIDs</span></span>

* <span data-ttu-id="fc184-147">Red Hat Enterprise Linux</span><span class="sxs-lookup"><span data-stu-id="fc184-147">Red Hat Enterprise Linux</span></span>
    * `rhel.7-x64`
* <span data-ttu-id="fc184-148">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="fc184-148">Ubuntu</span></span>
    * `ubuntu.14.04-x64`
    * `ubuntu.14.10-x64`
    * `ubuntu.15.04-x64`
    * `ubuntu.15.10-x64`
    * `ubuntu.16.04-x64`
    * `ubuntu.16.10-x64`
* <span data-ttu-id="fc184-149">CentOS</span><span class="sxs-lookup"><span data-stu-id="fc184-149">CentOS</span></span>
    * `centos.7-x64`
* <span data-ttu-id="fc184-150">Debian</span><span class="sxs-lookup"><span data-stu-id="fc184-150">Debian</span></span>
    * `debian.8-x64`
* <span data-ttu-id="fc184-151">Fedora</span><span class="sxs-lookup"><span data-stu-id="fc184-151">Fedora</span></span>
    * `fedora.23-x64`
    * `fedora.24-x64`
* <span data-ttu-id="fc184-152">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="fc184-152">OpenSUSE</span></span>
    * `opensuse.13.2-x64`
    * `opensuse.42.1-x64`
* <span data-ttu-id="fc184-153">Oracle Linux</span><span class="sxs-lookup"><span data-stu-id="fc184-153">Oracle Linux</span></span>
    * `ol.7-x64`
    * `ol.7.0-x64`
    * `ol.7.1-x64`
    * `ol.7.2-x64`
* <span data-ttu-id="fc184-154">Derivados do Ubuntu com suporte no momento</span><span class="sxs-lookup"><span data-stu-id="fc184-154">Currently supported Ubuntu derivatives</span></span> 
    * `linuxmint.17-x64`
    * `linuxmint.17.1-x64`
    * `linuxmint.17.2-x64`
    * `linuxmint.17.3-x64`
    * `linuxmint.18-x64`

## <a name="os-x-rids"></a><span data-ttu-id="fc184-155">RIDs do OS X</span><span class="sxs-lookup"><span data-stu-id="fc184-155">OS X RIDs</span></span>

* `osx.10.10-x64`
* `osx.10.11-x64`
* `osx.10.12-x64`

