---
title: 'Tutorial: Instale e use ferramentas locais do .NET Core'
description: Saiba como instalar e usar uma ferramenta .NET como ferramenta local.
ms.date: 02/12/2020
ms.openlocfilehash: a4355886513040e2436bdbd87905e5baee2dd7a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156693"
---
# <a name="tutorial-install-and-use-a-net-core-local-tool-using-the-net-core-cli"></a><span data-ttu-id="235c3-103">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="235c3-103">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>

<span data-ttu-id="235c3-104">**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="235c3-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="235c3-105">Este tutorial ensina como instalar e usar uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="235c3-105">This tutorial teaches you how to install and use a local tool.</span></span> <span data-ttu-id="235c3-106">Você usa uma ferramenta que você cria no [primeiro tutorial desta série](global-tools-how-to-create.md).</span><span class="sxs-lookup"><span data-stu-id="235c3-106">You use a tool that you create in the [first tutorial of this series](global-tools-how-to-create.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="235c3-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="235c3-107">Prerequisites</span></span>

* <span data-ttu-id="235c3-108">Complete o [primeiro tutorial desta série.](global-tools-how-to-create.md)</span><span class="sxs-lookup"><span data-stu-id="235c3-108">Complete the [first tutorial of this series](global-tools-how-to-create.md).</span></span>
* <span data-ttu-id="235c3-109">Instale o tempo de execução do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="235c3-109">Install the .NET Core 2.1 runtime.</span></span>

  <span data-ttu-id="235c3-110">Para este tutorial você instala e usa uma ferramenta que tem como alvo o .NET Core 2.1, então você precisa ter esse tempo de execução instalado em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="235c3-110">For this tutorial you install and use a tool that targets .NET Core 2.1, so you need to have that runtime installed on your machine.</span></span> <span data-ttu-id="235c3-111">Para instalar o tempo de execução 2.1, acesse a [página de download do .NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1) e encontre o link de instalação em tempo de execução na coluna Executar aplicativos - **Runtime.**</span><span class="sxs-lookup"><span data-stu-id="235c3-111">To install the 2.1 runtime, go to the [.NET Core 2.1 download page](https://dotnet.microsoft.com/download/dotnet-core/2.1) and find the runtime installation link in the **Run apps - Runtime** column.</span></span>

## <a name="create-a-manifest-file"></a><span data-ttu-id="235c3-112">Criar um arquivo manifesto</span><span class="sxs-lookup"><span data-stu-id="235c3-112">Create a manifest file</span></span>

<span data-ttu-id="235c3-113">Para instalar uma ferramenta apenas para acesso local (para o diretório atual e subdiretórios), ele precisa ser adicionado a um arquivo manifesto.</span><span class="sxs-lookup"><span data-stu-id="235c3-113">To install a tool for local access only (for the current directory and subdirectories), it has to be added to a manifest file.</span></span>

<span data-ttu-id="235c3-114">A partir da pasta *microsoft.botsay,* navegue até um nível até a pasta do *repositório:*</span><span class="sxs-lookup"><span data-stu-id="235c3-114">From the *microsoft.botsay* folder, navigate up one level to the *repository* folder:</span></span>

```console
cd ..
```

<span data-ttu-id="235c3-115">Crie um arquivo manifesto executando o novo comando [dotnet:](dotnet-new.md)</span><span class="sxs-lookup"><span data-stu-id="235c3-115">Create a manifest file by running the [dotnet new](dotnet-new.md) command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="235c3-116">A saída indica criação bem sucedida do arquivo.</span><span class="sxs-lookup"><span data-stu-id="235c3-116">The output indicates successful creation of the file.</span></span>

```console
The template "Dotnet local tool manifest file" was created successfully.
```

<span data-ttu-id="235c3-117">O arquivo *.config/dotnet-tools.json* ainda não tem ferramentas:</span><span class="sxs-lookup"><span data-stu-id="235c3-117">The *.config/dotnet-tools.json* file has no tools in it yet:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="235c3-118">As ferramentas listadas em um arquivo manifesto estão disponíveis para o diretório e subdiretórios atuais.</span><span class="sxs-lookup"><span data-stu-id="235c3-118">The tools listed in a manifest file are available to the current directory and subdirectories.</span></span> <span data-ttu-id="235c3-119">O diretório atual é aquele que contém o diretório *.config* com o arquivo manifesto.</span><span class="sxs-lookup"><span data-stu-id="235c3-119">The current directory is the one that contains the *.config* directory with the manifest file.</span></span>

<span data-ttu-id="235c3-120">Quando você usa um comando CLI que se refere a uma ferramenta local, o SDK procura um arquivo manifesto no diretório atual e diretórios-pai.</span><span class="sxs-lookup"><span data-stu-id="235c3-120">When you use a CLI command that refers to a local tool, the SDK searches for a manifest file in the current directory and parent directories.</span></span> <span data-ttu-id="235c3-121">Se ele encontrar um arquivo manifesto, mas o arquivo não incluir a ferramenta referenciada, ele continuará a pesquisa através de diretórios-mãe.</span><span class="sxs-lookup"><span data-stu-id="235c3-121">If it finds a manifest file, but the file doesn't include the referenced tool, it continues the search up through parent directories.</span></span> <span data-ttu-id="235c3-122">A pesquisa termina quando encontra a ferramenta referenciada `isRoot` ou `true`encontra um arquivo manifesto com set para .</span><span class="sxs-lookup"><span data-stu-id="235c3-122">The search ends when it finds the referenced tool or it finds a manifest file with `isRoot` set to `true`.</span></span>

## <a name="install-botsay-as-a-local-tool"></a><span data-ttu-id="235c3-123">Instale o botsay como uma ferramenta local</span><span class="sxs-lookup"><span data-stu-id="235c3-123">Install botsay as a local tool</span></span>

<span data-ttu-id="235c3-124">Instale a ferramenta a partir do pacote que você criou no primeiro tutorial:</span><span class="sxs-lookup"><span data-stu-id="235c3-124">Install the tool from the package that you created in the first tutorial:</span></span>

```dotnetcli
dotnet tool install --add-source ./microsoft.botsay/nupkg microsoft.botsay
```

<span data-ttu-id="235c3-125">Este comando adiciona a ferramenta ao arquivo manifesto que você criou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="235c3-125">This command adds the tool to the manifest file that you created in the preceding step.</span></span> <span data-ttu-id="235c3-126">A saída de comando mostra em qual arquivo manifesto a ferramenta recém-instalada está em:</span><span class="sxs-lookup"><span data-stu-id="235c3-126">The command output shows which manifest file the newly installed tool is in:</span></span>

 ```console
 You can invoke the tool from this directory using the following command:
 'dotnet tool run botsay' or 'dotnet botsay'
 Tool 'microsoft.botsay' (version '1.0.0') was successfully installed.
 Entry is added to the manifest file /home/name/repository/.config/dotnet-tools.json
 ```

<span data-ttu-id="235c3-127">O arquivo *.config/dotnet-tools.json* agora tem uma ferramenta:</span><span class="sxs-lookup"><span data-stu-id="235c3-127">The *.config/dotnet-tools.json* file now has one tool:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "microsoft.botsay": {
      "version": "1.0.0",
      "commands": [
        "botsay"
      ]
    }
  }
}
```

## <a name="use-the-tool"></a><span data-ttu-id="235c3-128">Usar a ferramenta</span><span class="sxs-lookup"><span data-stu-id="235c3-128">Use the tool</span></span>

<span data-ttu-id="235c3-129">Invoque a `dotnet tool run` ferramenta executando o comando da pasta do *repositório:*</span><span class="sxs-lookup"><span data-stu-id="235c3-129">Invoke the tool by running the `dotnet tool run` command from the *repository* folder:</span></span>

```dotnetcli
dotnet tool run botsay hello from the bot
```

## <a name="restore-a-local-tool-installed-by-others"></a><span data-ttu-id="235c3-130">Restaurar uma ferramenta local instalada por outros</span><span class="sxs-lookup"><span data-stu-id="235c3-130">Restore a local tool installed by others</span></span>

<span data-ttu-id="235c3-131">Você normalmente instala uma ferramenta local no diretório raiz do repositório.</span><span class="sxs-lookup"><span data-stu-id="235c3-131">You typically install a local tool in the root directory of the repository.</span></span> <span data-ttu-id="235c3-132">Depois de verificar o arquivo manifesto no repositório, outros desenvolvedores podem obter o arquivo manifesto mais recente.</span><span class="sxs-lookup"><span data-stu-id="235c3-132">After you check in the manifest file to the repository, other developers can get the latest manifest file.</span></span> <span data-ttu-id="235c3-133">Para instalar todas as ferramentas listadas no arquivo `dotnet tool restore` manifesto, eles podem executar um único comando.</span><span class="sxs-lookup"><span data-stu-id="235c3-133">To install all of the tools listed in the manifest file, they can run a single `dotnet tool restore` command.</span></span>

1. <span data-ttu-id="235c3-134">Abra o arquivo *.config/dotnet-tools.json* e substitua o conteúdo pelo seguinte JSON:</span><span class="sxs-lookup"><span data-stu-id="235c3-134">Open the *.config/dotnet-tools.json* file, and replace the contents with the following JSON:</span></span>

   ```json
   {
     "version": 1,
     "isRoot": true,
     "tools": {
       "microsoft.botsay": {
         "version": "1.0.0",
         "commands": [
           "botsay"
         ]
       },
       "dotnetsay": {
         "version": "2.1.3",
         "commands": [
           "dotnetsay"
         ]
       }
     }
   }
   ```

1. <span data-ttu-id="235c3-135">Substitua pelo `<name>` nome usado para criar o projeto.</span><span class="sxs-lookup"><span data-stu-id="235c3-135">Replace `<name>` with the name you used to create the project.</span></span>

1. <span data-ttu-id="235c3-136">Salve suas alterações.</span><span class="sxs-lookup"><span data-stu-id="235c3-136">Save your changes.</span></span>

   <span data-ttu-id="235c3-137">Fazer essa alteração é o mesmo que obter a versão mais recente `dotnetsay` do repositório depois que outra pessoa instalou o pacote para o diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="235c3-137">Making this change is the same as getting the latest version from the repository after someone else installed the package `dotnetsay` for the project directory.</span></span>

1. <span data-ttu-id="235c3-138">Execute o comando `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="235c3-138">Run the `dotnet tool restore` command.</span></span>

   ```dotnetcli
   dotnet tool restore
   ```

   <span data-ttu-id="235c3-139">O comando produz saída como o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="235c3-139">The command produces output like the following example:</span></span>

   ```console
   Tool 'microsoft.botsay' (version '1.0.0') was restored. Available commands: botsay
   Tool 'dotnetsay' (version '2.1.3') was restored. Available commands: dotnetsay
   Restore was successful.
   ```

1. <span data-ttu-id="235c3-140">Verifique se as ferramentas estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="235c3-140">Verify that the tools are available:</span></span>

   ```dotnetcli
   dotnet tool list
   ```

   <span data-ttu-id="235c3-141">A saída é uma lista de pacotes e comandos, semelhante ao seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="235c3-141">The output is a list of packages and commands, similar to the following example:</span></span>

   ```console
   Package Id      Version      Commands       Manifest
   --------------------------------------------------------------------------------------------
   microsoft.botsay 1.0.0        botsay         /home/name/repository/.config/dotnet-tools.json
   dotnetsay        2.1.3        dotnetsay      /home/name/repository/.config/dotnet-tools.json
   ```

1. <span data-ttu-id="235c3-142">Teste as ferramentas:</span><span class="sxs-lookup"><span data-stu-id="235c3-142">Test the tools:</span></span>

   ```dotnetcli
   dotnet tool run dotnetsay hello from dotnetsay
   dotnet tool run botsay hello from botsay
   ```

## <a name="update-a-local-tool"></a><span data-ttu-id="235c3-143">Atualize uma ferramenta local</span><span class="sxs-lookup"><span data-stu-id="235c3-143">Update a local tool</span></span>

<span data-ttu-id="235c3-144">A versão instalada da `dotnetsay` ferramenta local é 2.1.3.</span><span class="sxs-lookup"><span data-stu-id="235c3-144">The installed version of local tool `dotnetsay` is 2.1.3.</span></span>  <span data-ttu-id="235c3-145">A versão mais recente é 2.1.4.</span><span class="sxs-lookup"><span data-stu-id="235c3-145">The latest version is 2.1.4.</span></span> <span data-ttu-id="235c3-146">Use o comando [dotnet tool update](dotnet-tool-update.md) para atualizar a ferramenta para a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="235c3-146">Use the [dotnet tool update](dotnet-tool-update.md) command to update the tool to the latest version.</span></span>

```dotnetcli
dotnet tool update dotnetsay
```

<span data-ttu-id="235c3-147">A saída indica o novo número da versão:</span><span class="sxs-lookup"><span data-stu-id="235c3-147">The output indicates the new version number:</span></span>

```console
Tool 'dotnetsay' was successfully updated from version '2.1.3' to version '2.1.4'
(manifest file /home/name/repository/.config/dotnet-tools.json).
```

<span data-ttu-id="235c3-148">O comando update encontra o primeiro arquivo manifesto que contém o ID do pacote e o atualiza.</span><span class="sxs-lookup"><span data-stu-id="235c3-148">The update command finds the first manifest file that contains the package ID and updates it.</span></span> <span data-ttu-id="235c3-149">Se não houver tal ID de pacote em qualquer arquivo manifesto que esteja no escopo da pesquisa, o SDK adiciona uma nova entrada ao arquivo manifesto mais próximo.</span><span class="sxs-lookup"><span data-stu-id="235c3-149">If there is no such package ID in any manifest file that is in the scope of the search, the SDK adds a new entry to the closest manifest file.</span></span> <span data-ttu-id="235c3-150">O escopo de pesquisa é através de `isRoot = true` diretórios-mãe até que um arquivo manifesto seja encontrado.</span><span class="sxs-lookup"><span data-stu-id="235c3-150">The search scope is up through parent directories until a manifest file with `isRoot = true` is found.</span></span>

## <a name="remove-local-tools"></a><span data-ttu-id="235c3-151">Remover ferramentas locais</span><span class="sxs-lookup"><span data-stu-id="235c3-151">Remove local tools</span></span>

<span data-ttu-id="235c3-152">Remova as ferramentas instaladas executando o comando [de desinstalar a ferramenta dotnet:](dotnet-tool-uninstall.md)</span><span class="sxs-lookup"><span data-stu-id="235c3-152">Remove the installed tools by running the [dotnet tool uninstall](dotnet-tool-uninstall.md) command:</span></span>

```dotnetcli
dotnet tool uninstall microsoft.botsay
```

```dotnetcli
dotnet tool uninstall dotnetsay
```

## <a name="troubleshoot"></a><span data-ttu-id="235c3-153">Solucionar problemas</span><span class="sxs-lookup"><span data-stu-id="235c3-153">Troubleshoot</span></span>

<span data-ttu-id="235c3-154">Se você receber uma mensagem de erro ao seguir o tutorial, consulte [Problemas de uso da ferramenta .NET Core](troubleshoot-usage-issues.md).</span><span class="sxs-lookup"><span data-stu-id="235c3-154">If you get an error message while following the tutorial, see [Troubleshoot .NET Core tool usage issues](troubleshoot-usage-issues.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="235c3-155">Confira também</span><span class="sxs-lookup"><span data-stu-id="235c3-155">See also</span></span>

<span data-ttu-id="235c3-156">Para obter mais informações, consulte [as ferramentas .NET Core](global-tools.md)</span><span class="sxs-lookup"><span data-stu-id="235c3-156">For more information, see [.NET Core tools](global-tools.md)</span></span>
