---
title: Publicar um pacote NuGet
description: Práticas recomendadas para a publicação bibliotecas .NET NuGet.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0602712311411ef3d59825bec8c5e550bc8d8265
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2018
ms.locfileid: "49369677"
---
# <a name="publishing-a-nuget-package"></a><span data-ttu-id="7e807-103">Publicar um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="7e807-103">Publishing a NuGet package</span></span>

<span data-ttu-id="7e807-104">Pacotes do NuGet são publicados e consumidos de repositórios de pacote.</span><span class="sxs-lookup"><span data-stu-id="7e807-104">NuGet packages are published and consumed from package repositories.</span></span> <span data-ttu-id="7e807-105">Enquanto o NuGet.org é a mais amplamente conhecido e usado de repositório, há muitos lugares para publicar pacotes do NuGet:</span><span class="sxs-lookup"><span data-stu-id="7e807-105">While NuGet.org is the most widely known and used repository, there are many places to publish NuGet packages:</span></span>

* <span data-ttu-id="7e807-106">**[NuGet.org](https://www.nuget.org/)**  é o principal repositório online para pacotes do NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e807-106">**[NuGet.org](https://www.nuget.org/)** is the primary online repository for NuGet packages.</span></span> <span data-ttu-id="7e807-107">Todos os pacotes em NuGet.org estão publicamente disponíveis para todos.</span><span class="sxs-lookup"><span data-stu-id="7e807-107">All packages on NuGet.org are publicly available to everyone.</span></span> <span data-ttu-id="7e807-108">Por padrão, o Visual Studio tem NuGet.org como uma origem de pacote e para muitos desenvolvedores NuGet.org é o repositório de pacote somente com que eles poderá interagir.</span><span class="sxs-lookup"><span data-stu-id="7e807-108">By default, Visual Studio has NuGet.org as a package source and for many developers NuGet.org is the only package repository they'll interact with.</span></span> <span data-ttu-id="7e807-109">NuGet.org é o melhor lugar para publicar pacotes estáveis e pacotes de pré-lançamento que você deseja comentários da comunidade no.</span><span class="sxs-lookup"><span data-stu-id="7e807-109">NuGet.org is the best place to publish stable packages and pre-release packages that you want community feedback on.</span></span>

* <span data-ttu-id="7e807-110">**[MyGet](https://myget.org/)**  dá suporte ao serviço de repositório [feeds de pacote personalizado gratuito para projetos de código-fonte aberto](https://www.myget.org/opensource).</span><span class="sxs-lookup"><span data-stu-id="7e807-110">**[MyGet](https://myget.org/)** repository service supports [free custom package feeds for open-source projects](https://www.myget.org/opensource).</span></span> <span data-ttu-id="7e807-111">Um feed personalizado do MyGet público é um lugar ideal para publicar pacotes de pré-lançamento criados pelo seu serviço de CI.</span><span class="sxs-lookup"><span data-stu-id="7e807-111">A MyGet public custom feed is an ideal place to publish pre-release packages created by your CI service.</span></span> <span data-ttu-id="7e807-112">MyGet também fornece feeds privados comercialmente.</span><span class="sxs-lookup"><span data-stu-id="7e807-112">MyGet also provides private feeds commercially.</span></span>

* <span data-ttu-id="7e807-113">Um **[feed local](/nuget/hosting-packages/local-feeds)** permite que você trate uma pasta como um repositório de pacotes e torna o `*.nupkg` arquivos na pasta acessível pelo NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e807-113">A **[local feed](/nuget/hosting-packages/local-feeds)** allows you to treat a folder like a package repository and makes the `*.nupkg` files in the folder accessible by NuGet.</span></span> <span data-ttu-id="7e807-114">Um feed local é útil para testar um pacote do NuGet antes de publicá-lo em NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="7e807-114">A local feed is useful for testing a NuGet package before publishing it to NuGet.org.</span></span>

> [!NOTE]
> <span data-ttu-id="7e807-115">NuGet.org [não permite que um pacote a ser excluído](/nuget/policies/deleting-packages) depois que ele é carregado.</span><span class="sxs-lookup"><span data-stu-id="7e807-115">NuGet.org [does not allow a package to be deleted](/nuget/policies/deleting-packages) once it is uploaded.</span></span> <span data-ttu-id="7e807-116">Um pacote pode ser removido da lista para que não é publicamente visível na interface do usuário, mas o `*.nupkg` ainda pode ser baixado na restauração.</span><span class="sxs-lookup"><span data-stu-id="7e807-116">A package can be unlisted so that it is not publicly visible in the UI but the `*.nupkg` can still be downloaded on restore.</span></span> <span data-ttu-id="7e807-117">Além disso, o nuget.org não permite a versões de pacote duplicado.</span><span class="sxs-lookup"><span data-stu-id="7e807-117">Also, nuget.org does not allow duplicate package versions.</span></span> <span data-ttu-id="7e807-118">Para corrigir um pacote do NuGet com um erro que você precise remover o pacote incorreto da lista, aumente o número de versão e publicar uma nova versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="7e807-118">To correct a NuGet package with an error you have to unlist the incorrect package, increment the version number and publish a new version of the package.</span></span>

<span data-ttu-id="7e807-119">**FAZER ✔️** [publicar pacotes estáveis e pacotes de pré-lançamento](/nuget/create-packages/publish-a-package) desejar comentários da comunidade do logon no NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="7e807-119">**✔️ DO** [publish stable packages and pre-release packages](/nuget/create-packages/publish-a-package) you want community feedback on to NuGet.org.</span></span>

<span data-ttu-id="7e807-120">**Considere a possibilidade de ✔️** publicar pacotes de pré-lançamento para uma MyGet feed de um build de integração contínua.</span><span class="sxs-lookup"><span data-stu-id="7e807-120">**✔️ CONSIDER** publishing pre-release packages to a MyGet feed from a continuous integration build.</span></span>

<span data-ttu-id="7e807-121">**Considere a possibilidade de ✔️** testar pacotes no ambiente de desenvolvimento usando um feed local ou MyGet.</span><span class="sxs-lookup"><span data-stu-id="7e807-121">**✔️ CONSIDER** testing packages in your development environment using a local feed or MyGet.</span></span> <span data-ttu-id="7e807-122">Verifique o pacote funciona em seguida, publique-o em NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="7e807-122">Check the package works then publish it to NuGet.org.</span></span>

## <a name="nugetorg-security"></a><span data-ttu-id="7e807-123">Segurança de NuGet.org</span><span class="sxs-lookup"><span data-stu-id="7e807-123">NuGet.org security</span></span>

<span data-ttu-id="7e807-124">É importante que os atores ruins não é possível acessar sua conta do NuGet e carregar uma versão mal-intencionado da sua biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7e807-124">It's important that bad actors can't access your NuGet account and upload a malicious version of your library.</span></span> <span data-ttu-id="7e807-125">NuGet.org oferece dois fatores autenticação e notificações por email quando um pacote é publicado.</span><span class="sxs-lookup"><span data-stu-id="7e807-125">NuGet.org offers two-factor authentication and email notifications when a package is published.</span></span> <span data-ttu-id="7e807-126">Habilitar esses recursos após fazer logon no NuGet.org sobre o **configurações de conta** página.</span><span class="sxs-lookup"><span data-stu-id="7e807-126">Enable these features after logging into NuGet.org on the **Account settings** page.</span></span>

<span data-ttu-id="7e807-127">![texto ALT](./media/publish-nuget-package/nuget-2fa.png "NuGet segurança da conta")</span><span class="sxs-lookup"><span data-stu-id="7e807-127">![alt text](./media/publish-nuget-package/nuget-2fa.png "NuGet Account Security")</span></span>

<span data-ttu-id="7e807-128">**FAZER ✔️** usa uma conta da Microsoft para entrar NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e807-128">**✔️ DO** use a Microsoft account to sign in to NuGet.</span></span>

<span data-ttu-id="7e807-129">**FAZER ✔️** habilitar a autenticação de dois fatores para acessar o NuGet.</span><span class="sxs-lookup"><span data-stu-id="7e807-129">**✔️ DO** enable two-factor authentication for accessing NuGet.</span></span>

<span data-ttu-id="7e807-130">**FAZER ✔️** habilitar notificação por email quando um pacote é publicado.</span><span class="sxs-lookup"><span data-stu-id="7e807-130">**✔️ DO** enable email notification when a package is published.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7e807-131">[Anterior](./sourcelink.md)
[Próximo](./versioning.md)</span><span class="sxs-lookup"><span data-stu-id="7e807-131">[Previous](./sourcelink.md)
[Next](./versioning.md)</span></span>
