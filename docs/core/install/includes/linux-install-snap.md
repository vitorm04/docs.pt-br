---
ms.openlocfilehash: 5e77b7bd73c09e061a94a29703cf5286814d1ebb
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602911"
---

[<span data-ttu-id="5575b-101">O .NET Core está disponível no repositório de snap.</span><span class="sxs-lookup"><span data-stu-id="5575b-101">.NET Core is available from the Snap Store.</span></span>](https://snapcraft.io/dotnet-sdk)

<span data-ttu-id="5575b-102">Um snap é um pacote de um aplicativo e suas dependências que funcionam sem modificação em várias distribuições do Linux diferentes.</span><span class="sxs-lookup"><span data-stu-id="5575b-102">A snap is a bundle of an app and its dependencies that works without modification across many different Linux distributions.</span></span> <span data-ttu-id="5575b-103">Os snaps são detectáveis e instaláveis no repositório de instantâneos.</span><span class="sxs-lookup"><span data-stu-id="5575b-103">Snaps are discoverable and installable from the Snap Store.</span></span> <span data-ttu-id="5575b-104">Para obter mais informações sobre o snap, consulte [introdução ao snap](https://snapcraft.io/docs/getting-started).</span><span class="sxs-lookup"><span data-stu-id="5575b-104">For more information about Snap, see [Getting started with Snap](https://snapcraft.io/docs/getting-started).</span></span>

<span data-ttu-id="5575b-105">Somente as versões com suporte do .NET Core estão disponíveis por meio do snap.</span><span class="sxs-lookup"><span data-stu-id="5575b-105">Only supported versions of .NET Core are available through Snap.</span></span>

### <a name="install-the-sdk"></a><span data-ttu-id="5575b-106">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="5575b-106">Install the SDK</span></span>

<span data-ttu-id="5575b-107">Pacotes snap para SDK do .NET Core são todos publicados sob o mesmo identificador: `dotnet-sdk` .</span><span class="sxs-lookup"><span data-stu-id="5575b-107">Snap packages for .NET Core SDK are all published under the same identifier: `dotnet-sdk`.</span></span> <span data-ttu-id="5575b-108">Uma versão específica do SDK pode ser instalada especificando o canal.</span><span class="sxs-lookup"><span data-stu-id="5575b-108">A specific version of the SDK can be installed by specifying the channel.</span></span> <span data-ttu-id="5575b-109">O SDK inclui o tempo de execução de coresponder.</span><span class="sxs-lookup"><span data-stu-id="5575b-109">The SDK includes the coresponding runtime.</span></span> <span data-ttu-id="5575b-110">A tabela a seguir lista os canais:</span><span class="sxs-lookup"><span data-stu-id="5575b-110">The following table list the channels:</span></span>

| <span data-ttu-id="5575b-111">Versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5575b-111">.NET Core version</span></span> | <span data-ttu-id="5575b-112">Ajustar pacote</span><span class="sxs-lookup"><span data-stu-id="5575b-112">Snap package</span></span>             |
|-------------------|--------------------------|
| <span data-ttu-id="5575b-113">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5575b-113">3.1 (LTS)</span></span>         | <span data-ttu-id="5575b-114">`3.1` ou `latest/stable`</span><span class="sxs-lookup"><span data-stu-id="5575b-114">`3.1` or `latest/stable`</span></span> |
| <span data-ttu-id="5575b-115">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5575b-115">2.1 (LTS)</span></span>         | `2.1`                    |
| <span data-ttu-id="5575b-116">Versão prévia do .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="5575b-116">.NET 5.0 preview</span></span>  | `5.0/beta`               |

<span data-ttu-id="5575b-117">Use o `snap install` comando para instalar um pacote de snap SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5575b-117">Use the `snap install` command to install a .NET Core SDK snap package.</span></span> <span data-ttu-id="5575b-118">Use o `--channel` parâmetro para indicar qual versão deve ser instalada.</span><span class="sxs-lookup"><span data-stu-id="5575b-118">Use the `--channel` parameter to indicate which version to install.</span></span> <span data-ttu-id="5575b-119">Se esse parâmetro for omitido, `latest/stable` será usado.</span><span class="sxs-lookup"><span data-stu-id="5575b-119">If this parameter is omitted, `latest/stable` is used.</span></span> <span data-ttu-id="5575b-120">Neste exemplo, `3.1` é especificado:</span><span class="sxs-lookup"><span data-stu-id="5575b-120">In this example, `3.1` is specified:</span></span>

```bash
sudo snap install dotnet-sdk --classic --channel=3.1
```

<span data-ttu-id="5575b-121">Em seguida, registre o `dotnet` comando para o sistema com o `snap alias` comando:</span><span class="sxs-lookup"><span data-stu-id="5575b-121">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-sdk.dotnet dotnet
```

<span data-ttu-id="5575b-122">Este comando é formatado como: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="5575b-122">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="5575b-123">Você pode escolher qualquer `{alias}` nome que desejar.</span><span class="sxs-lookup"><span data-stu-id="5575b-123">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="5575b-124">Por exemplo, você pode nomear o comando após a versão específica instalada pelo snap: `sudo snap alias dotnet-sdk.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="5575b-124">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-sdk.dotnet dotnet31`.</span></span> <span data-ttu-id="5575b-125">Ao usar o comando `dotnet31` , você invocará essa versão específica do .net.</span><span class="sxs-lookup"><span data-stu-id="5575b-125">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="5575b-126">Mas isso é incompatível com a maioria dos tutoriais e exemplos, pois eles esperam que um `dotnet` comando esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="5575b-126">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="install-the-runtime"></a><span data-ttu-id="5575b-127">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="5575b-127">Install the runtime</span></span>

<span data-ttu-id="5575b-128">Os pacotes snap para o tempo de execução do .NET Core são publicados em seu próprio identificador de pacote.</span><span class="sxs-lookup"><span data-stu-id="5575b-128">Snap packages for .NET Core Runtime are each published under their own package identifier.</span></span> <span data-ttu-id="5575b-129">A tabela a seguir lista os identificadores de pacote:</span><span class="sxs-lookup"><span data-stu-id="5575b-129">The following table lists the package identifiers:</span></span>

| <span data-ttu-id="5575b-130">Versão do .NET Core</span><span class="sxs-lookup"><span data-stu-id="5575b-130">.NET Core version</span></span> | <span data-ttu-id="5575b-131">Ajustar pacote</span><span class="sxs-lookup"><span data-stu-id="5575b-131">Snap package</span></span>        |
|-------------------|---------------------|
| <span data-ttu-id="5575b-132">3,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5575b-132">3.1 (LTS)</span></span>         | `dotnet-runtime-31` |
| <span data-ttu-id="5575b-133">3.0</span><span class="sxs-lookup"><span data-stu-id="5575b-133">3.0</span></span>               | `dotnet-runtime-30` |
| <span data-ttu-id="5575b-134">2.2</span><span class="sxs-lookup"><span data-stu-id="5575b-134">2.2</span></span>               | `dotnet-runtime-22` |
| <span data-ttu-id="5575b-135">2,1 (LTS)</span><span class="sxs-lookup"><span data-stu-id="5575b-135">2.1 (LTS)</span></span>         | `dotnet-runtime-21` |

<span data-ttu-id="5575b-136">Use o `snap install` comando para instalar um pacote de snap do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5575b-136">Use the `snap install` command to install a .NET Core Runtime snap package.</span></span> <span data-ttu-id="5575b-137">Neste exemplo, o .NET Core 3,1 está instalado:</span><span class="sxs-lookup"><span data-stu-id="5575b-137">In this example, .NET Core 3.1 is installed:</span></span>

```bash
sudo snap install dotnet-runtime-31 --classic
```

<span data-ttu-id="5575b-138">Em seguida, registre o `dotnet` comando para o sistema com o `snap alias` comando:</span><span class="sxs-lookup"><span data-stu-id="5575b-138">Next, register the `dotnet` command for the system with the `snap alias` command:</span></span>

```bash
sudo snap alias dotnet-runtime-31.dotnet dotnet
```

<span data-ttu-id="5575b-139">Este comando é formatado como: `sudo snap alias {package}.{command} {alias}` .</span><span class="sxs-lookup"><span data-stu-id="5575b-139">This command is formatted as: `sudo snap alias {package}.{command} {alias}`.</span></span> <span data-ttu-id="5575b-140">Você pode escolher qualquer `{alias}` nome que desejar.</span><span class="sxs-lookup"><span data-stu-id="5575b-140">You can choose any `{alias}` name you would like.</span></span> <span data-ttu-id="5575b-141">Por exemplo, você pode nomear o comando após a versão específica instalada pelo snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31` .</span><span class="sxs-lookup"><span data-stu-id="5575b-141">For example, you could name the command after the specific version installed by snap: `sudo snap alias dotnet-runtime-31.dotnet dotnet31`.</span></span> <span data-ttu-id="5575b-142">Ao usar o comando `dotnet31` , você invocará essa versão específica do .net.</span><span class="sxs-lookup"><span data-stu-id="5575b-142">When you use the command `dotnet31`, you'll invoke this specific version of .NET.</span></span> <span data-ttu-id="5575b-143">Mas isso é incompatível com a maioria dos tutoriais e exemplos, pois eles esperam que um `dotnet` comando esteja disponível.</span><span class="sxs-lookup"><span data-stu-id="5575b-143">But this is incompatible with most tutorials and examples as they expect a `dotnet` command to be available.</span></span>

### <a name="ssl-certificate-errors"></a><span data-ttu-id="5575b-144">Erros de certificado SSL</span><span class="sxs-lookup"><span data-stu-id="5575b-144">SSL Certificate errors</span></span>

<span data-ttu-id="5575b-145">Quando o .NET é instalado por meio do snap, é possível que, em alguns distribuições, os certificados SSL do .NET possam não ser encontrados e você receba um erro semelhante ao seguinte durante `restore` :</span><span class="sxs-lookup"><span data-stu-id="5575b-145">When .NET is installed through Snap, it's possible that on some distros the .NET SSL certificates may not be found and you may receive an error similar to the following during `restore`:</span></span>

```bash
Processing post-creation actions...
Running 'dotnet restore' on /home/myhome/test/test.csproj...
  Restoring packages for /home/myhome/test/test.csproj...
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error : Unable to load the service index for source https://api.nuget.org/v3/index.json. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The SSL connection could not be established, see inner exception. [/home/myhome/test/test.csproj]
/snap/dotnet-sdk/27/sdk/2.2.103/NuGet.targets(114,5): error :   The remote certificate is invalid according to the validation procedure. [/home/myhome/test/test.csproj]
```

<span data-ttu-id="5575b-146">Para resolver esse problema, defina algumas variáveis ambiente:</span><span class="sxs-lookup"><span data-stu-id="5575b-146">To resolve this issue, set a few enviornment variables:</span></span>

```bash
export SSL_CERT_FILE=[path-to-certificate-file]
export SSL_CERT_DIR=/dev/null
```

<span data-ttu-id="5575b-147">O local do certificado variará de acordo com distribuição.</span><span class="sxs-lookup"><span data-stu-id="5575b-147">The certificate location will vary by distro.</span></span> <span data-ttu-id="5575b-148">Aqui estão os locais para o distribuições onde tivemos o problema.</span><span class="sxs-lookup"><span data-stu-id="5575b-148">Here are the locations for the distros where we have experienced the issue.</span></span>

* <span data-ttu-id="5575b-149">Fedora`/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="5575b-149">Fedora - `/etc/pki/ca-trust/extracted/pem/tls-ca-bundle.pem`</span></span>
* <span data-ttu-id="5575b-150">OpenSUSE`/etc/ssl/ca-bundle.pem`</span><span class="sxs-lookup"><span data-stu-id="5575b-150">OpenSUSE - `/etc/ssl/ca-bundle.pem`</span></span>
* <span data-ttu-id="5575b-151">Solus -`/etc/ssl/certs/ca-certificates.crt`</span><span class="sxs-lookup"><span data-stu-id="5575b-151">Solus - `/etc/ssl/certs/ca-certificates.crt`</span></span>
