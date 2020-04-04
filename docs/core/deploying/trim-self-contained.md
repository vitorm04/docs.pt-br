---
title: Aparar aplicações independentes
description: Aprenda a aparar aplicativos autônomos para reduzir seu tamanho. O .NET Core empacota o tempo de execução com um aplicativo que é publicado independente mente e geralmente inclui mais tempo de execução do que é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 01/23/2020
ms.openlocfilehash: 5206ca255c500b382402ac4e7dd3300b7face1cf
ms.sourcegitcommit: 45cced471d59d5dac3f0c92abc9d4849716098a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/04/2020
ms.locfileid: "80665631"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="81093-104">Apare implantações e executáveis autônomos</span><span class="sxs-lookup"><span data-stu-id="81093-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="81093-105">Ao publicar um aplicativo independente, o tempo de execução do .NET Core é empacotado com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81093-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="81093-106">Este agrupamento adiciona uma quantidade significativa de conteúdo ao seu aplicativo embalado.</span><span class="sxs-lookup"><span data-stu-id="81093-106">This bundling adds a significant amount of content to your packaged application.</span></span>

<span data-ttu-id="81093-107">Quando se trata de implantar seu aplicativo, o tamanho muitas vezes é um fator importante.</span><span class="sxs-lookup"><span data-stu-id="81093-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="81093-108">Manter o tamanho do aplicativo do pacote o menor possível é tipicamente uma meta para os desenvolvedores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="81093-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="81093-109">Dependendo da complexidade do aplicativo, apenas um subconjunto do tempo de execução é necessário para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="81093-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="81093-110">Estas partes não utilizadas do tempo de execução são desnecessárias e podem ser cortadas da aplicação embalada.</span><span class="sxs-lookup"><span data-stu-id="81093-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

> [!NOTE]
> <span data-ttu-id="81093-111">Trimming é um recurso experimental no .NET Core 3.1 e _só_ está disponível para aplicativos que são publicados independentes.</span><span class="sxs-lookup"><span data-stu-id="81093-111">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="trim-your-application"></a><span data-ttu-id="81093-112">Apare sua aplicação</span><span class="sxs-lookup"><span data-stu-id="81093-112">Trim your application</span></span>

<span data-ttu-id="81093-113">O exemplo a seguir mostra como aparar seu aplicativo usando o comando [dotnet publish:](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="81093-113">The following example shows how to trim your application using the [dotnet publish](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true /p:PublishSingleFile=false /p:PublishTrimmed=true
```

<span data-ttu-id="81093-114">O recurso de corte funciona examinando os binários de aplicativos para descobrir e construir um gráfico dos conjuntos de tempo de execução necessários.</span><span class="sxs-lookup"><span data-stu-id="81093-114">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="81093-115">As montagens restantes de tempo de execução que não são referenciadas são aparadas.</span><span class="sxs-lookup"><span data-stu-id="81093-115">The remaining runtime assemblies that aren't referenced are trimmed.</span></span>

## <a name="trimming-issues-when-using-reflection"></a><span data-ttu-id="81093-116">Questões de corte ao usar reflexão</span><span class="sxs-lookup"><span data-stu-id="81093-116">Trimming issues when using reflection</span></span>

<span data-ttu-id="81093-117">Existem cenários em que a funcionalidade de corte falhará em detectar referências.</span><span class="sxs-lookup"><span data-stu-id="81093-117">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="81093-118">Por exemplo, um aplicativo que usa reflexão pode esbarrar nessa questão porque a dependência do conjunto só será conhecida em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="81093-118">For example, an application that uses reflection could run into this issue because the dependency on the assembly will only be known at run time.</span></span>

<span data-ttu-id="81093-119">O corte só é um problema se o uso do reflexo depender de um conjunto de tempo de execução que não seja referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="81093-119">Trimming is only a problem if the reflection usage depends on a runtime assembly that isn't referenced directly.</span></span> <span data-ttu-id="81093-120">Tenha em mente que seu código de aplicativo pode não estar usando reflexão diretamente, mas uma montagem de terceiros que você está fazendo referência pode estar usando-o.</span><span class="sxs-lookup"><span data-stu-id="81093-120">Keep in mind that your application code may not be using reflection directly, but a third-party assembly you're referencing may be using it.</span></span>

<span data-ttu-id="81093-121">Quando o código está fazendo referência a uma API através da reflexão e você não quer que o linker corte o conjunto que contém essa API, você pode modificar seu arquivo de projeto para excluir o conjunto do processo de corte.</span><span class="sxs-lookup"><span data-stu-id="81093-121">When the code is referencing an API through reflection and you don't want the linker to trim the assembly that contains that API, you can modify your project file to exclude the assembly from the trimming process.</span></span> <span data-ttu-id="81093-122">O exemplo a seguir mostra `System.Security` como evitar que uma assembléia chamada seja aparada:</span><span class="sxs-lookup"><span data-stu-id="81093-122">The following example shows how to prevent an assembly called `System.Security` from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="see-also"></a><span data-ttu-id="81093-123">Confira também</span><span class="sxs-lookup"><span data-stu-id="81093-123">See also</span></span>

- [<span data-ttu-id="81093-124">Implantação de aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="81093-124">.NET Core application deployment</span></span>](index.md)
